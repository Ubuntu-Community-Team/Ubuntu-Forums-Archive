---
title: "OpenGL Segfaults"
date: 2008-05-27
forum: General Help
---

### Post by spiraloid on 2008-05-27
Hello,

**EDIT:*** The solution was simply this: I was initializing GLEW in the wrong place. For future reference and anyone else who runs into this problem. In my case, I am using GLFW. I was calling glewInit before glfw was fully initialized. It is best to create your GLFW or GLUT windows first, then call glewInit() in between that and your OpenGL initialization. The key GLEW error to watch for: Missing GL version.*

I couldn't figure out which of the myriad forums available on this site was most appropriate for my problem so I'm hoping this will be fine. I'm having an interesting problem and I'm hoping somebody out there can help me with it. I'm doing a bit of programming, just simple little test programs, and for the most part they run (when I get the code right ^.^). However, there are a few OpenGL commands which are reliably producing a segfault on two different machines with similar setups. Those OpenGL commands are:

glCreateShader()
glCreateProgram()
glIsProgram()
glIsShader()

and probably more. I've traced these down with GDB. If I remove the code which contains those commands from the software, it runs without error. But the moment I call any of those, the program will segfault. It could be something as simple as:

GLuint tmp = 0;
if (glIsProgram(tmp)) cout << "tmp is a program (oddly..)" << endl;

I am using the nvidia restricted drivers.

Machine 1: AMD64 Desktop running Ubuntu 8.04 amd64
Kernel: 2.6.24-17
Video Card: nVidia GeForce 8800 GTS

Machine 2: Intel Centrino Duo Laptop running Ubuntu 8.04 i386
Kernel: 2.6.24-16
Video Card: nVidia GeForce Go 7900

I know to properly help me with this more information will be needed. At this point though I am not sure what that information is, so let me know and I'll post it ASAP.

Thanks.

---

### Post by crazyfuturamanoob on 2008-05-27
im having opengl problems, but what was
you problem? my problems are like that
sometimes when running opengl apps i get
a hard freeze, or it will log out and go
to the login menu with no questions, instantly.

---

