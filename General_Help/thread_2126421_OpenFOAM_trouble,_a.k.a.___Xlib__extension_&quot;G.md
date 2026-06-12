---
title: "OpenFOAM trouble, a.k.a.   Xlib:  extension &quot;GLX&quot; missing on display &quot;:0&quot;."
date: 2013-03-17
forum: General Help
---

### Post by goldbeard on 2013-03-17
Hello.

This is the first time I have not found a solution in an existing thread. So here goes...

I just installed Ubuntu LTS 12.04 64 bit on a brand new custom computer. 

Specs are according to Ubuntu's System>Details>
15.4 GB RAM
i7-3770 CPU @3.40GHz x 8
Graphics Unknown (But I know it is a Nvidia Geforce GTX 690)
64 bit
1.9 TB


 I dual booted it on a second hard drive with Windows 7 on a different hard drive. Everything works great.
I installed Ubuntu to run [OpenFOAM]("http://www.openfoam.com/")  [http://www.openfoam.com/](http://www.openfoam.com/) . After following the instuctions on the website here [http://www.openfoam.org/download/ubuntu.php](http://www.openfoam.org/download/ubuntu.php), and watching a tutorial on youtube here [http://www.youtube.com/watch?v=AJESwh-QfSo](http://www.youtube.com/watch?v=AJESwh-QfSo).... I still get this message when trying to open the visualizing program paraFoam.


Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
ERROR: In /home/opencfd/OpenFOAM/ThirdParty-2.1.x/ParaView-3.12.0/VTK/Rendering/vtkXOpenGLRenderWindow.cxx, line 404
vtkXOpenGLRenderWindow (0x1d56990): Could not find a decent visual



Xlib:  extension "GLX" missing on display ":0".
ERROR: In /home/opencfd/OpenFOAM/ThirdParty-2.1.x/ParaView-3.12.0/VTK/Rendering/vtkXOpenGLRenderWindow.cxx, line 609
vtkXOpenGLRenderWindow (0x1d56990): GLX not found.  Aborting.


Aborted (core dumped)





I have tried Additional Drivers. No luck. I have read about disabling the Graphics card, which is a GeForce GTX 690 and I want to use it. I found a driver at nvidia here [http://www.nvidia.in/object/linux-display-ia32-295.49-driver-in.html](http://www.nvidia.in/object/linux-display-ia32-295.49-driver-in.html) but I can not find a program to open it.

I am using the program for fluid dynamic simulations for high performance hydrofoil design, so I want to harness as much power from the graphics card as possible.

If you need more info from my I am happy to give it. This is for work, and is very important. Help me, please.

Respectfully,

Goldbeard

---

### Post by goldbeard on 2013-03-20
Fixed it. Now how do I change the thread header to solved?

---

### Post by mojim on 2013-06-20
Hello there! Would you mind sharing how you solved this issue (about OpenFOAM...), because I am facing a similar situation! You will save me a lot of effort!  
Thank you!

---

