cmake_minimum_required(VERSION "3.22")

# Indicate the compliation environment (Host OS and CPU Arch): uname -s
# set(CMAKE_SYSTEM_NAME Darwin)
# set(CMAKE_SYSTEM_NAME FreeBSD)
set(CMAKE_SYSTEM_PROCESSOR x86_64)

# -----------------------------------------------------------------------------
# Define project name. After this, we can use "${PROJECT_NAME}" var to 
# dereference/re-use the project name as a String value.
#
# More details from here:
# https://cmake.org/cmake/help/v3.0/command/project.html?highlight=project
# -----------------------------------------------------------------------------
project("cpp_unit_test")


# -----------------------------------------------------------------------------
# Enable verbose makefile
# -----------------------------------------------------------------------------
set(CMAKE_VERBOSE_MAKEFILE TRUE)


# -----------------------------------------------------------------------------
# Enables testing for this directory and below.
# -----------------------------------------------------------------------------
enable_testing()
find_package(GTest REQUIRED)


# -----------------------------------------------------------------------------
# Compile and build executable
#
# `add_executable`: Adds an executable target called <name> to be built from the
#                   source files listed in the command invocation.
#
# syntax: add_executable(<name> [WIN32] [MACOSX_BUNDLE]
#              [EXCLUDE_FROM_ALL]
#              source1 [source2 ...])
#
# More details from here:
# https://cmake.org/cmake/help/v3.0/command/add_executable.html?highlight=add_executable
# -----------------------------------------------------------------------------
add_executable("${PROJECT_NAME}"     "src/main.cpp")
target_link_libraries("${PROJECT_NAME}" GTest::gtest GTest::gtest_main)
add_test(RunAllTestIn"${PROJECT_NAME}" "${PROJECT_NAME}")



# -----------------------------------------------------------------------------
# Print out cmake vars for debugging `MakeLists.txt` purpose
# -----------------------------------------------------------------------------
message(">>> CMAKE_SYSTEM_NAME: ${CMAKE_SYSTEM_NAME}")
message(">>> CMAKE_BUILD_TYPE: ${CMAKE_BUILD_TYPE}")
message(">>> CMAKE_C_COMPILER: ${CMAKE_CXX_COMPILER}")
message(">>> CMAKE_C_FLAGS: ${CMAKE_CXX_FLAGS}")
message(">>> CMAKE_C_FLAGS_DEBUG: ${CMAKE_CXX_FLAGS_DEBUG}")
message(">>> CMAKE_C_FLAGS_RELEASE: ${CMAKE_CXX_FLAGS_RELEASE}")
message(">>> GTest_FOUND: ${GTest_FOUND}")


