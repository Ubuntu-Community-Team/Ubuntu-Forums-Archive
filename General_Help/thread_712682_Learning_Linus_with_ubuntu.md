---
title: "Learning Linus with ubuntu"
date: 2008-03-01
forum: General Help
---

### Post by deamon_knight on 2008-03-01
I'm using Ubuntu to get into Linux and I like it, and I'm trying to learn more, but I need advice. Ubuntu as a desktop environment is great, I'm actively trying to sell my friends on switching, but I'm trying to go deeper. Installing from source gets me confused. I understand in broad strokes whats going on here, but I don't know what to do when problems occur.

Example, I'm trying to install Vulcan chess:

[http://www.fzort.org/mpr/projects/vulcan/](http://www.fzort.org/mpr/projects/vulcan/)

 I got the tar.gz and unzipped it says to sudo "make install". Usually this works for me, but in this case I get 2 pages of errors. I think I need an open GL source/package/library , and the readme says

 "You need OpenGL and X libraries and header files installed.  As of version 0.5, you also need libpng."

There are alot of OpenGL and X results when I search with Synaptic. I don't understand how to Identify what I need. Any advice.

I'm also trying to approach another problem. There is no memtest for Apple computers as far as I can tell. An easy solution should be to compile a vanilla Kernel with the smallest Memory Usage and memtester, and create a bootable image of that. However, I don't know how to do this! Where should I start looking?

---

### Post by amingv on 2008-03-02
Issue this command, it will give you all you need:

```
sudo apt-get install libpng12-dev xorg-dev freeglut3-dev
```

---

### Post by 3rdalbum on 2008-03-02
deamon_knight: When you try to compile something and it tells you that you're missing a particular package or a set of packages, what it needs is the "-dev" packages. For instance, if it tells you that you need "libpng", it really means that it needs something with "libpng" at the beginning of the name, and "-dev" at the end. Preferably the one with the highest version number.

I hope this illuminates things for you.

---

