---
title: "cannot find -lGL compiling Urho3d"
date: 2014-05-09
forum: General Help
---

### Post by vivienneanthony on 2014-05-09
Hi

I'm trying to compile Urho3D on my computer. I'm stuck because I'm getting the same exact problem someone else had and I don't know how to resolve it.

The link to the message is [https://code.google.com/p/urho3d/issues/detail?id=117](https://code.google.com/p/urho3d/issues/detail?id=117)

The package is at [http://urho3d.github.io/](http://urho3d.github.io/)

Any help will be appreciated

Vivienne


> **What steps will reproduce the problem?**
1. Compile with cmake gcc on ubuntu x64 system
2. error on link urho3d : /usr/bin/ld: cannot find -lGL

**3.**

**What is the expected output? What do you see instead?**
[ 76%] Building CXX object Engine/Engine/CMakeFiles/Engine.dir/CoreAPI.cpp.o
[ 76%] Building CXX object Engine/Engine/CMakeFiles/Engine.dir/PhysicsAPI.cpp.o
[ 76%] Building CXX object Engine/Engine/CMakeFiles/Engine.dir/ScriptAPI.cpp.o
[ 76%] Building CXX object Engine/Engine/CMakeFiles/Engine.dir/Precompiled.cpp.o
[ 77%] Building CXX object Engine/Engine/CMakeFiles/Engine.dir/EngineAPI.cpp.o
[ 77%] Building CXX object Engine/Engine/CMakeFiles/Engine.dir/UIAPI.cpp.o
Linking CXX static library libEngine.a
[ 77%] Built target Engine
[ 77%] Building CXX object Urho3D/CMakeFiles/Urho3D.dir/Urho3D.cpp.o
Linking CXX executable Urho3D
/usr/bin/ld: ne peut trouver -lGL
collect2: erreur: ld a retourné 1 code d'état d'exécution
make[2]: *** [Urho3D/Urho3D] Erreur 1
make[1]: *** [Urho3D/CMakeFiles/Urho3D.dir/all] Erreur 2
make: *** [all] Erreur 2


My compile does

[ 51%] Built target AngelScript
[ 51%] Built target GLEW
[ 52%] Built target LibCpuId
[ 79%] Built target Urho3D
Linking CXX executable /media/home2/vivienne/urho3d-Urho3D-59ef932/Bin/Urho3DPlayer
/usr/bin/ld.bfd.real: cannot find -lGL
collect2: ld returned 1 exit status
make[2]: *** [/media/home2/vivienne/urho3d-Urho3D-59ef932/Bin/Urho3DPlayer] Error 1
make[1]: *** [Tools/Urho3DPlayer/CMakeFiles/Urho3DPlayer.dir/all] Error 2
make: *** [all] Error 2




**My system is running in 64bit**
vivienne@vivienne-System-Product-Name:/usr/lib$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:        12.04
Codename:       precise

I know to compile I need to get a 32bit version of openGL development library and headers

---

