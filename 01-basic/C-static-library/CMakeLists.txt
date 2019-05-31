cmake_minimum_required(VERSION 3.5)

project(hello_library)

############################################################
# Create a library
############################################################

#Generate the static library from the library sources
#add_library(hello_library STATIC
#    src/Hello.cpp
#)
add_library( mylib SHARED IMPORTED )
set_target_properties( mylib PROPERTIES IMPORTED_LOCATION ${CMAKE_BINARY_DIR}/libhello_library.a )



############################################################
# Create an executable
############################################################
#target_include_directories(hello_library
#        PUBLIC
#        ${PROJECT_SOURCE_DIR}/include
#        )

# Add an executable with the above sources
include_directories(include/static/)
add_executable(hello_binary 
    src/main.cpp
)
TARGET_LINK_LIBRARIES(hello_binary mylib)
# link the new hello_library target with the hello_binary target
#target_link_libraries( hello_binary
#    PRIVATE
#        hello_library
#)
#TARGET_LINK_LIBRARIES(hello_binary libhello_library.a)

#target_link_libraries(hello_binary libhello_library.a)