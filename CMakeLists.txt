cmake_minimum_required(VERSION 3.14 FATAL_ERROR)

project(http-server LANGUAGES CXX)

# Standard C++20 ONLY
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED TRUE)
set(CMAKE_CXX_EXTENSIONS OFF)
if(MSVC)
    add_compile_options(/Gm- /MP /Zc:preprocessor /INCREMENTAL:NO)
endif()

# Project Options
option(WARNINGS_AS_ERRORS "Treat warnings as errors" ON)

# Compiler Warnings
include(tools/cmake/CompilerWarnings.cmake)

# Update Submodules
include(tools/cmake/UpdateSubmodules.cmake)

add_executable(http-server src/main.cpp)

target_compile_features(http-server PUBLIC cxx_std_20)
target_include_directories(http-server PRIVATE "src")
