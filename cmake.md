# Invoke
```
cd path/to/src
mkdir build
cd build
cmake -DCMAKE_EXPORT_COMPILE_COMMANDS=1 ..
make -j
```

# Finding packages

Install `pkgconfig`

```
brew install pkgconfig
```

# Set a variable
```
set(VARNAME VALUE)
```

Getting help on a module, not all modules have this
```
cmake --help-module findglew
```

Add a package
```
find_package(PkgConfig REQUIRED)
pkg_search_module(GLFW REQUIRED glfw3)
target include_directories(${TARGET} PUBLIC ${GLFW_INCLUDE_DIRS})
target_link_libraries(${TARGET} ${GLFW_LIBRARIES})
```

# Debugging CMake
Add print statements
```
message(STATUS "GLEW_FOUND=${GLEW_FOUND}")
```

Print all variables in current directory
https://stackoverflow.com/questions/9298278/cmake-print-out-all-accessible-variables-in-a-script
```
get_cmake_property(_variableNames VARIABLES)
list (SORT _variableNames)
foreach (_variableName ${_variableNames})
    message(STATUS "${_variableName}=${${_variableName}}")
endforeach()
```

# Build debug version of application
```
cmake -DCMAKE_BUILD_TYPE=Debug
```

# LSP support for C++ / clangd
```
cmake -DCMAKE_EXPORT_COMPILE_COMMANDS=1
```

