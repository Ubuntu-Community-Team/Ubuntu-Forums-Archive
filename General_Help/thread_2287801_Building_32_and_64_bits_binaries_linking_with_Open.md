---
title: "Building 32 and 64 bits binaries linking with OpenGL"
date: 2015-07-22
forum: General Help
---

### Post by arty0 on 2015-07-22
Hi,

So I've been struggling with this for a couple days now.
I need to be able to link with either 32bit or 64bit opengl on the same machine.

The problem is I can't seem to be able to install both.
I've installed nvidia-current-dev which contains both 32 and 64 bits libraries (but I have to symlink them to be able to link) but the amd64 and i386 packages of libglu1-mesa-dev are apparently mutually exclusive.
It appears to be a known bug, too ([https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1246013](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1246013) [https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1317113](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1317113) [https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/949606](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/949606)).

So is there a workaround that would let me build what I need without failing at link time?
Any help much welcome, thanks in advance.

---

### Post by 3246251196 on 2015-07-22
The programming section is where this will end up.

When I run an application that needs my 32 bit opengl library I just set LD_LIBRARY_PATH.

This environment variable takes precedence - so if I would do something like export LD_LIBRARY_PATH=/usr/lib/opengl (not the real path) - but then, when trying to locate a library if it finds it in the dir set in the env var it will take that one!

---

### Post by arty0 on 2015-07-23
I hesitated with the programming section but this seems more like a package issue to me, so I ended up posting here instead.
If a mod sees this, sorry and feel free to move it where you see fit.

So yeah, I know about ld preloading. Unfortunately, this works for the driver but not for libglu and other libraries that uninstall each other's architecture. :(

---

