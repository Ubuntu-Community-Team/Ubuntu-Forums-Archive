---
title: "Soname issues with libglfw3 (wrong version name)"
date: 2017-01-27
forum: General Help
---

### Post by lvrma on 2017-01-27
Hey guys!

I'm having an issue with, as the title states, libglfw3. The problem is I'm trying to build the OpenGL Superbible's project, but it has countless references when linking to -lglfw3, and Ubuntu refers to it as simply -lglfw (stated by *sudo pkg-config --libs glfw3* itself, running the same command to just glfw tells me it's not installed).

Not even a project-wide refactor using CLion (and replacing all references to -lglfw3 with -lglfw) was able to fix the issue, and I don't think manually changing the sonames is a good idea.

Any suggestions on how to overcome this? Maybe create a symlink to -lglfw3 that leads to -lglfw somehow?
I have 3 .so files currently:
libglfw.so, libglfw.so.3, libglfw.so.3.1
and the packages libglfw3:amd64 and libglfw3-dev:amd64, and nothing else related to libglfw at all, no older versions, nothing.

---

### Post by lvrma on 2017-01-27
Nevermind!! Problem solved LOL
Turns out manually changing the sonames WAS the answer.
I just copied the libglfw.so file to a clone named libglfw3.so, both having their SONAME being libglfw.so.3 as indicated by objdump -p
Well, this can be marked as **SOLVED**, but &#8203;hopefully will help someone else in the future

---

