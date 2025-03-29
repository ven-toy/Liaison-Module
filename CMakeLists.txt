# Modules/ModuleName/CMakeLists.txt

# Create a static library for the module
add_library(ModuleName STATIC
    Source/module.cpp
    Source/module.h
    # Add additional source files as necessary
)

# Specify the public include directory for the module
target_include_directories(ModuleName PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/Include
)

# Link dependencies, if any (e.g., linking with the Core library)
target_link_libraries(ModuleName PRIVATE Core)

# Optional: Set compile options for stricter warnings
if(MSVC)
    target_compile_options(ModuleName PRIVATE /W4)
else()
    target_compile_options(ModuleName PRIVATE -Wall -Wextra -pedantic)
endif()
