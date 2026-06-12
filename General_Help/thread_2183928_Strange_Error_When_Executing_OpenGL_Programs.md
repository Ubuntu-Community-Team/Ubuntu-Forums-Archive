---
title: "Strange Error When Executing OpenGL Programs"
date: 2013-10-26
forum: General Help
---

### Post by mrmoss on 2013-10-26
I just did a fresh install of 13.10 64 bit.  Whenever I try to run an OpenGL/Glut/Glew compiled c++ program I get the following error:

```
Inconsistency detected by ld.so: dl-version.c: 224: _dl_check_map_versions: Assertion `needed != ((void *)0)' failed!
```

These are programs I've written a long time ago and work fine on a dozen other machines and before I upgraded.  I installed all the necessary packages (freeglut3-dev, libglu1-mesa-dev, and libglew-dev).

I've tried searching on Google, there are a few hits, but none have solutions!

Any ideas?!
Mike

---

### Post by kevin.dorange on 2013-10-28
I have exactly the same error running every OpenGL application I compile.
I use GL without GLU/GLUT/GLEW, I link my code with X libraries, Xrandr and pnglib.
I also just upgraded to 13.10 64.

An interesting point is that it did not seem to happen before I used proprietary GPU driver. On the "Softwares & Updates" program, I switched from :
**Using X.Org X server -- Nouveau display driver from xserver-xorg-video-nouveau (open source)**
to
[B]Using NVIDIA binary Xorg driver, kernel modules and VDPAU library from nvidia-319 (proprietary, tested)
[/B]
"Softwares & Updates" also provides **319-updates**, **304** and **304-updates**. I'll check them.
EDIT : the same error for every of these versions :(

It's important for me to have one of proprietary drivers working as open source driver does not support a version of GLSL which is recent enough.

---

### Post by cszwrj on 2013-11-04
Got the exactly same error here. I am on Nvidia 331.17 and glew 1.9. The opensource driver is working fine as @kevin.dorange mentioned.

There are 2 interesting things I noticed:

1. the old binary compiled from the same code on 12.04 works without problem on the new system. But when I try to compile it again on 13.10 the error popup.

2. If I don't use any extension and stick with opengl 1.2, there will be no error. It seems like the error only appear when glew is used to access the extensions.

---

### Post by henrikn on 2013-11-04
I just happened to try building my old OpenGL programs yesterday, and ran into this problem as well. I haven't investigated it much, other than googling and finding references of this assert going back far (in other contexts). It only seems to happen with GLEW. When I use another library to access extensions everything works fine.

---

### Post by jarod1860 on 2013-11-11
same error on ubuntu 13.10

---

### Post by biri on 2013-11-20
Same error on ubuntu 13.10 and with all NVIDIA binary Xorg driver 304, 204-update, 319, 319-update. 
Graphic card :  GeForce GTX 570/PCIe/SSE2
Removing glew (and using instead #define  GL_GLEXT_PROTOTYPES) did not change anything ... In my opinion it might be related with some advanced GL function (i succeeded in launching a old GL program).
EDIT : In fact not, it might be related to link problem between c++ standard lib and GL. See below :

Trying to execute this simple program :
```
[FONT=system]#include <string>[/FONT]
[FONT=system]#include <GL/gl.h>[/FONT]
[FONT=system]#include <GL/glut.h>[/FONT]
[FONT=system]
[/FONT]
[FONT=system]static void displayFunc(void){[/FONT]
[FONT=system]    glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);[/FONT]
[FONT=system]    glutSwapBuffers();[/FONT]
[FONT=system]}[/FONT]
[FONT=system]
[/FONT][FONT=system]int main(int argc,char **argv){ [/FONT]
[FONT=system]    std::string nimportequoi;[/FONT]

[FONT=system]    glutInit(&argc, argv);[/FONT]
[FONT=system]    glutInitDisplayMode(GLUT_RGBA | GLUT_DOUBLE | GLUT_DEPTH);[/FONT]

[FONT=system]    if(glutCreateWindow("") == 0) return 1;[/FONT]

[FONT=system]    /// Specification de la fonction d'affichage[/FONT]
[FONT=system]    glutDisplayFunc(displayFunc);[/FONT]

[FONT=system]    //printf("Un programme simple !\n");[/FONT]
[FONT=system]    glutMainLoop();[/FONT]

[FONT=system]    return 0;[/FONT]
[FONT=system]}[/FONT]
```
give me the same error. 
If I comment the std::string the program works. The linker must be doing something strange...

---

### Post by arealperson on 2014-04-21
Its my understanding that this is a bug in 13.10 and UP, Your out of luck. no one currently has a solution.
maybe someday in the future you'll be able to compile OpenGL on Ubuntu.

I've just installed 14.04 and have the same problem.

You might try...sudo 
$ sudo ln -s /usr/lib/nvidia-319/libGL.so /usr/lib/x86_64-linux-gnu/

But that will only work for a few people.

My advise is 'delete Ubuntu' and revert to 12.04.

If someone knows how to fix this , it would be nice if they would post the solution
or point to a URL

---

