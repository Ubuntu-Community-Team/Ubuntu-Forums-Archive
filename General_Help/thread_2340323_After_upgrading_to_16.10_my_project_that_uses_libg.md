---
title: "After upgrading to 16.10 my project that uses libglfw3 will not build"
date: 2016-10-17
forum: General Help
---

### Post by maggymoo on 2016-10-17
Hi,

I just upgraded from Ubuntu 16.04 to 16.10.
I have a C++ OpenGL project that uses glfw (libglfw3 package).
It was building correctly before the upgrade.

This is output from cmake when I build:
```

/usr/bin/ld: //usr/local/lib/libglfw3.a(context.c.o): relocation R_X86_64_32S against `.rodata' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: //usr/local/lib/libglfw3.a(init.c.o): relocation R_X86_64_32S against `.rodata' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: //usr/local/lib/libglfw3.a(input.c.o): relocation R_X86_64_32 against `.rodata' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: //usr/local/lib/libglfw3.a(monitor.c.o): relocation R_X86_64_32 against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: //usr/local/lib/libglfw3.a(window.c.o): relocation R_X86_64_32 against `.rodata' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: //usr/local/lib/libglfw3.a(x11_init.c.o): relocation R_X86_64_32S against `.rodata' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: //usr/local/lib/libglfw3.a(x11_joystick.c.o): relocation R_X86_64_32S against undefined symbol `_glfw' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: //usr/local/lib/libglfw3.a(x11_monitor.c.o): relocation R_X86_64_32 against `.rodata' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: //usr/local/lib/libglfw3.a(x11_window.c.o): relocation R_X86_64_32S against undefined symbol `_glfw' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: //usr/local/lib/libglfw3.a(x11_unicode.c.o): relocation R_X86_64_32S against `.data' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: //usr/local/lib/libglfw3.a(glx_context.c.o): relocation R_X86_64_32 against `.rodata' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: //usr/local/lib/libglfw3.a(gamma.c.o): relocation R_X86_64_32 against `.rodata' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: //usr/local/lib/libglfw3.a(x11_clipboard.c.o): relocation R_X86_64_32 against `.rodata' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: final link failed: Nonrepresentable section on output
collect2: error: ld returned 1 exit status
CMakeFiles/Explorer.dir/build.make:408: recipe for target '../bin/Explorer' failed
make[2]: *** [../bin/Explorer] Error 1
make[1]: *** [CMakeFiles/Explorer.dir/all] Error 2
CMakeFiles/Makefile2:67: recipe for target 'CMakeFiles/Explorer.dir/all' failed
Makefile:83: recipe for target 'all' failed
make: *** [all] Error 2
[vscode] CMake exited with status 2

```

This is my CMakeList.txt (if it's helpful):
```
cmake_minimum_required (VERSION 2.6)
project (Explorer)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)

set (CMAKE_CXX_STANDARD 14)

include_directories(include)

find_package(PkgConfig REQUIRED)
pkg_search_module(GLFW REQUIRED glfw3)

find_package(OpenGL REQUIRED)
if(NOT OPENGL_FOUND)
    message("Error: OpenGL not found")
endif(NOT OPENGL_FOUND)

include_directories(${OPENGL_INCLUDE_DIRS} ${GLFW_INCLUDE_DIRS})

add_executable(Explorer
    src/Application.h
    src/Application.cpp
    src/Camera.h
    src/Camera.cpp
    src/Explorer.h
    src/Explorer.cpp
    src/lodepng.h
    src/lodepng.cpp
    src/main.cpp
    src/PerlinNoise.h
    src/PerlinNoise.cpp
    src/Player.h
    src/Player.cpp
    src/Program.h
    src/Program.cpp
    src/Shader.h
    src/Shader.cpp
    src/Terrain.h
    src/Terrain.cpp
    src/Grass.h
    src/Grass.cpp
    src/Texture.h
    src/Texture.cpp)

add_custom_command(TARGET Explorer PRE_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_directory
    ${CMAKE_SOURCE_DIR}/res $<TARGET_FILE_DIR:Explorer>)

target_link_libraries(Explorer ${OPENGL_LIBRARIES} ${GLFW_STATIC_LIBRARIES})

```

It looks like glfw supports 16.10:
[http://packages.ubuntu.com/yakkety/libglfw3](http://packages.ubuntu.com/yakkety/libglfw3)

My understanding of CMake is that I shouldn't have to "recompile with -fPIC".
[B]
Any ideas what might be going on here?
[/B]
If this isn't the appropriate place to ask, I apologise.

Thanks,
Magnus

---

