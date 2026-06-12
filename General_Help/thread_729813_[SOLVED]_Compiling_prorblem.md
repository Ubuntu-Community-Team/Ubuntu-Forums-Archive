---
title: "[SOLVED] Compiling prorblem"
date: 2008-03-20
forum: General Help
---

### Post by desertboy on 2008-03-20
:Edit solved see last post

Trying to compile a program that need these

 - Qt >= 4.2
 - FreePascal >= 1.9.4
 - SDL >= 1.2.5
 - SDL_net >= 1.2.5
 - SDL_mixer >= 1.2
 - SDL_image >= 1.2
 - SDL_ttf >= 2.0
 - CMake >= 2.4.4

How do I install them all when I try to compile I get this

-- Check for working CXX compiler: /usr/bin/g++
CMake Error: your CXX compiler: "/usr/bin/g++" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
CMake Error: Internal CMake error, TryCompile configure of cmake failed
-- Check for working CXX compiler: /usr/bin/g++ -- broken
CMake Error: The C++ compiler "/usr/bin/g++" is not able to compile a simple test program.
It fails with the following output:
 

CMake will not be able to correctly generate this project.
CMake Error: your CXX compiler: "/usr/bin/g++" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
-- Configuring done


I've tried opening synaptic and ticking anything vaguely relevant and installing any help would be appreciated.

---

### Post by HermanAB on 2008-03-20
I think you need to install the "gcc-c++" package from synaptic.

Cheers,

Herman

---

### Post by ryanhaigh on 2008-03-20
```
sudo apt-get install build-essential
```

That should take care of the g++ issue as well as make and some other 'essentials' for compiling code.

What application are you trying to compile? You will need to do a little research but you may find ```
apt-get build-dep <packagename>
``` useful.

---

### Post by desertboy on 2008-03-20
Thanks I'm trying to compile hedgewars from SVN

I now get this far

Free Pascal Compiler version 2.0.4 [2007/02/02] for i386
Copyright (c) 1993-2006 by Florian Klaempfl
Target OS: Linux for i386
Compiling /home/stuart/hedgewars/hedgewars/hwengine.dpr
Compiling SDLh.pas
Fatal: Can't find unit GL
Fatal: Compilation aborted
Error: /usr/bin/ppc386 returned an error exitcode (normal if you did not specify a source file to be compiled)
make[2]: *** [bin/hwengine] Error 1
make[1]: *** [hedgewars/CMakeFiles/hwengine.dir/all] Error 2
make: *** [all] Error 2

---

### Post by ryanhaigh on 2008-03-20
Considering that it is in the repos you may have some luck with ```
sudo apt-get build-dep hedgewars
```

---

### Post by desertboy on 2008-03-20
> **ryanhaigh said:**
> Considering that it is in the repos you may have some luck with ```
sudo apt-get build-dep hedgewars
```

Thanks I tried that as soon as I read you first post it installed a load of stuff and now I get this far which is a lot further than it was going before.

---

### Post by mc4man on 2008-03-20
if you did the build-dep and still no luck try  cmake -i   and follow prompts (double check on paths if needed)

---

### Post by desertboy on 2008-03-22
Solved, missing package

fp-utils-gfx

---

