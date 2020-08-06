cmake_minimum_required(VERSION 3.5)
project(kaleidoscope_lang)

find_package(LLVM REQUIRED CONFIG)

message(STATUS "Found LLVM ${LLVM_PACKAGE_VERSION}")
message(STATUS "Using LLVMConfig.cmake in: ${LLVM_DIR}")

include_directories(${LLVM_INCLUDE_DIRS})
add_definitions(${LLVM_DEFINITIONS})

# Find the libraries that correspond to the LLVM components
# that we wish to use
llvm_map_components_to_libnames(llvm_libs core)

file(GLOB HEADERS "*.h")
file(GLOB SOURCES "*.cpp")

add_executable(kaleidoscope_lang ${HEADERS} ${SOURCES})
target_link_libraries(kaleidoscope_lang ${llvm_libs})
