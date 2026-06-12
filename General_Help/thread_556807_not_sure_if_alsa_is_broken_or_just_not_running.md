---
title: "not sure if alsa is broken or just not running"
date: 2007-09-21
forum: General Help
---

### Post by chocolatetoothpaste on 2007-09-21
Ok, I have a small situation.  First a little background:  i am running ubuntu 7.04.  I did a command line install, and I am setting up a very light weight system with open box and a few kde and gnome apps installed (no DE, just the base libs to run the apps).  I am setting this up on a Gateway MT3705 laptop, which previously had sound issues.  A patch was issued however, which fixes the sound.  When I was running KDE, i was able to download and install the ALSA patch/upgrade, but since reformatting and building a lightweight system, i have been unsuccessful at getting sound to work.  So, i'm just wondering if someone can help me trouble shoot this and get it working.  I'm not even sure how to check that alsa is running, or determine which version.  Any help would be greatly appreciated!

---

### Post by chocolatetoothpaste on 2007-09-21
erm, bump.

---

### Post by chocolatetoothpaste on 2007-09-22
OK, just a short update.  I ran the patch file to update to alsa1.0.15rc1, and while attempting to compile, it gave me this notice towards the end of compilation:
```

The file /usr/src/linux/include/linux/version.h does not exist.  Please install the package with the full kernel sources for your distribution or use --with-kernel=dir option to specify another direcotry with kernel sources (default is /usr/src/linux).

```I think it's safe to assume that I am missing some kernel header files required to build that package, my question is which ones?

Edit:

Well, I'm sorry no one was able to help me.  But, I have fixed my problem.  For some reason my kernel headers didn't get upgraded when i did apt-get upgrade, so I had to run
```

sudo apt-get install linux-headers-$(uname -r)

```
and that installed the correct headers.  I was then able to compile alsa, and reload the modules; voila!  i have sound!  Just a general question about compiling:  could i do './conigure && make' on one machine, then copy the dir to another before doing 'sudo make install'?  After compiling, I always feel like there is a lot of junk that gets left behind on my computer, and I worry about what files it's edited that it shouldn't have etc.  Let me know if this is possible, or if I am just paranoid.

---

