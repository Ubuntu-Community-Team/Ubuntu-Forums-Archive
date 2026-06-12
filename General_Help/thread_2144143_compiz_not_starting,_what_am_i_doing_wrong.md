---
title: "compiz not starting, what am i doing wrong?"
date: 2013-05-11
forum: General Help
---

### Post by JoinTheRealms on 2013-05-11
Hey guys, im trying to get compiz working Asus transformer tf300t, i dont know if anyones familiar with the install process but its basically mounting a virtual image of a distro, in this case xubuntu. Just to note compiz does work on this device, one of the devolpers over at xda developers has a ubuntu image in which compiz works fine with unity but fails exactly the same when trying to use it with gnome(classic)  

Im using compiz --replace as root, but it unloads the running window manager and stops loading compiz at the line below, and stays there until i ctrl c it. I wasnt going to bother asking as i thought it would be an advanced issue that was device specific but i just tried the same thing on my ubuntu 13.04 x64 pc and i done the exact same thing.

compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : ini
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : default


If someone could point me in the right direction i would be hugely greatful, ive been trying to get this to work for a few weeks now...... lol

Cheers:)

---

### Post by CatKiller on 2013-05-11
I doubt it'll actually solve your problem in any way, but don't run compiz as root.

---

### Post by JoinTheRealms on 2013-05-11
> **CatKiller said:**
> I doubt it'll actually solve your problem in any way, but don't run compiz as root.

Thanks for the suggestion , its got me closer to the problem. Im now getting spammed with to main errors 

compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
libEGL warning: DRI2: failed to authenticate
Compiz (opengl) - Fatal: GL_OES_EGL_image is missing

---

### Post by CatKiller on 2013-05-12
You'll probably also need to check for things in your Home directory being erroneously owned by root from running things that way when you shouldn't.

---

### Post by pootan on 2013-05-12
I just recently did this using this guide I found.

Maybe your problems are originating at number 3.
[http://www.webupd8.org/2012/11/how-to-set-up-compiz-in-xubuntu-1210-or.html](http://www.webupd8.org/2012/11/how-to-set-up-compiz-in-xubuntu-1210-or.html)

---

