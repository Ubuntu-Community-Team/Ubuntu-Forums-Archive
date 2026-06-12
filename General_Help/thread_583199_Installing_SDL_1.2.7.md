---
title: "Installing SDL 1.2.7"
date: 2007-10-20
forum: General Help
---

### Post by soluphobe on 2007-10-20
I'm having issues installing SDL 1.2.7.  I have no internet on the machine in question, so I downloaded the package from sourceforge and tried to install it (the unzipped folder is on my desktop).  I run```
./configure --prefix=/usr --disable-debug
```and I get a long chain of stuff ending in Error 1.  That's happened to me before, but I looked through the output and I found some issue with ESD.  The output says that SDL can't find the esd-config script, and that I should alter my path variable.

The interesting thing is that I'm trying to install SDL so I can play brutalchess.  Whenever I try to run ```
./configure
``` in brutalchess, I get the EXACT same error, except that ESD is replaced by SDL.

So when I try to install brutalchess, I get a message saying it can't find the sdl-config file (and that therefore sdl doesn't exits), but when I try to install SDL, I get a message saying that it can't find the esd-config file (and that therefore esd doesn't exist).  I've never installed ESD, but doesn't it come standard with the system?

---

### Post by soluphobe on 2007-10-22
*bump*

Okay.  Got internet on the machine in question.  This may sound like a stupid question, but what command do I run to install SDL from the repositories?  sudo apt-get install sdl1.2.7 ?


Thanks!

---

### Post by ihcnet on 2007-10-22
Try running Synaptic when you're not quite sure of the exact package name, it has a search feature. To install sdl ```
sudo apt-get install libsdl1.2debian
``` however, version 1.2.11 is in the repositories.

---

### Post by soluphobe on 2007-10-22
Thanks.  I've never actually been able to get online before, so I've never bothered with synaptic or anything.

---

