cmake_minimum_required(VERSION 2.8.9)
project(directory_test)

#Bring the headers, such as Student.h into the project
include_directories(include)
include_directories(out)

add_custom_command(OUTPUT out.txt
  DEPENDS in.txt
  COMMAND cp in.txt out.txt
  COMMENT "Copying clang's ...")

add_custom_target(run ALL
  DEPENDS out.txt)

set (CMAKE_CXX_STANDARD 11)

#Can manually add the sources using the set command as follows:
set(SOURCES src/mainapp.cpp src/Student.cpp)

#However, the file(GLOB...) allows for wildcard additions:
file(GLOB SOURCES "src/*.cpp")

add_executable(testStudent ${SOURCES})
