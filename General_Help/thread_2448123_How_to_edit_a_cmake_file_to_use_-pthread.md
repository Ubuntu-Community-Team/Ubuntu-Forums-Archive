---
title: "How to edit a cmake file to use -pthread"
date: 2020-08-02
forum: General Help
---

### Post by jcdenton1995 on 2020-08-02
Hello all,

Basically I'm trying to compile a .so file from source but every time it's compiled and the program tries to load it I get the following error...```
UI-Console Error:  dlopen('/usr/lib/x86_64-linux-gnu/mupen64plus/mupen64plus-video-GLideN64.so')  failed:  /usr/lib/x86_64-linux-gnu/mupen64plus/mupen64plus-video-GLideN64.so:  undefined symbol: pthread_create
  UI-Console Error: Specified Video plugin not found: /usr/lib/x86_64-linux-gnu/mupen64plus/mupen64plus-video-GLideN64.so


```...basically I've been told I might need to pass '-pthread' when compiling, but it uses a makefile and I don't know which source files it uses, can anyone tell me the syntax to use and where in the file to put it? Or if anyone has any other suggestions that would be great too. Thanks!

---

### Post by TheFu on 2020-08-03
Seems the first step might be to actually post the Makefile?  Just a guess.  I can help with Make, but not with cmake.  And be certain to use an editor that doesn't touch tabs or spaces. In a Makefile, a tab matters and 4 spaces is NOT the same.

---

### Post by jcdenton1995 on 2020-08-04
> **TheFu said:**
> Seems the first step might be to actually post the Makefile?  Just a guess.  I can help with Make, but not with cmake.  And be certain to use an editor that doesn't touch tabs or spaces. In a Makefile, a tab matters and 4 spaces is NOT the same.

Thanks! I'm afraid it is built with cmake, how would I post the file? As it is quite long, would I just dump it in-between some code tags?

---

### Post by TheFu on 2020-08-04
> **jcdenton1995 said:**
> Thanks! I'm afraid it is built with cmake, how would I post the file? As it is quite long, would I just dump it in-between some code tags?

Depends on what "quite long" means.  If more than 2 pgs, I'd use paste.ubuntu.com and provide a link.  May want to edit the first post to clearly say cmake too.

---

### Post by mrbig99 on 2020-08-06
I don't know about you, but this plugin was previously working for me fine in  19.04 and 19.10, but stopped working in 20.04.  Even though it hasn't been updated in a while it still works better than all the older ones.  So I was searching for  this same issue and came upon this thread.  I gathered the same as you  that libpthread now needs to be linked into the so for some reason, and I  figured out how to do it in Cmake.  Basically change the last lines of  the /src/CMakeLists.txt file like the following and then build the  library again (CMake, then Make). I verifid with ldd that the old binary didn't have a libpthread dependency, and the new one does.  I admit to not entirely knowing what I'm doing here and it being a quick hack, but the only thing that matters is the plugin is working for me again.

```
  [B]set(THREADS_PREFER_PTHREAD_FLAG ON)
  find_package(Threads REQUIRED)
[/B]
  if(SDL)
    if (NOHQ)
      target_link_libraries(${GLideN64_DLL_NAME} **PRIVATE Threads::Threads** ${OPENGL_LIBRARIES} ${SDL_LIBRARIES} ${FREETYPE_LIBRARIES} osal )
    else (NOHQ)
      target_link_libraries(${GLideN64_DLL_NAME} **PRIVATE Threads::Threads** ${OPENGL_LIBRARIES} ${SDL_LIBRARIES} ${FREETYPE_LIBRARIES} osal GLideNHQ )
    endif (NOHQ)
  else(SDL)
    if (NOHQ)
      target_link_libraries(${GLideN64_DLL_NAME} **PRIVATE Threads::Threads** ${OPENGL_LIBRARIES} ${FREETYPE_LIBRARIES} osal )
    else (NOHQ)
      target_link_libraries(${GLideN64_DLL_NAME} **PRIVATE Threads::Threads** ${OPENGL_LIBRARIES} ${FREETYPE_LIBRARIES} osal GLideNHQ )
    endif (NOHQ)
  endif(SDL)
endif( CMAKE_BUILD_TYPE STREQUAL "Release")
```

---

### Post by jcdenton1995 on 2020-08-10
@mrbig99 Hi there, thanks for coming back with this, I actually managed to just sort of make it work (much like you say you did) but I actually used another method, which I will share for future reference!

Basically I opened "../GLideN64_Public_Release_4_0/src/build/CMakeCache.txt" and found the following text to which I just appended "-pthread"```
//Flags used by the CXX compiler during all build types.
CMAKE_CXX_FLAGS:STRING=-pthread

```I then simply ran the command to compile the package and it worked!

I don't know which way is better as it was honestly just a complete stab in the dark, or an educated guess. I believe I might have to remove "-pthread" before I next compile a package with CMake as I'm not ceratin weather that file is created by CMake and read every time a package is compiled, or if it is specific to the package who's directory it is found in (i.e GLideN64)

Thanks for sharing your method too!

---

### Post by TheFu on 2020-08-10
Best to mark solved issues as "SOLVED"  using the "Thread Tools" button near the top.  Help out the community - PLEASE.

---

### Post by jcdenton1995 on 2020-08-11
No worries, I thought I had done this!

---

