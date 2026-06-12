---
title: "Desktop effects could not be enabled."
date: 2008-05-17
forum: General Help
---

### Post by xTorvos on 2008-05-17
BACKGROUND:  I am extremely new to Linux.  I have tried a couple distros on other my spare computers, but then I never use them and end up reinstalling windows.  However, when I go to college I feel that I am going to need some in depth knowledge of at least a couple distros.  Therefore, I want to do a 3-month trial and only use Linux.  At the moment I'm using Ubuntu 8.04.

PROBLEM:  I was trying to get started by making my desktop prettier.  The first thing I tried was System>Preferences>Appearance.  When I try to enable it, I get the error stating that "Desktop effects could not be enabled."  What could be causing this and what can a newbie such as I do in order to fix it and my my desktop pretty?

INFORMATION:  Dell Vostro 1400, Nvidia 8400 GS, Penryn 9300 C2D, 1GB DDR2 667.

---

### Post by badfish591 on 2008-05-17
is your graphics driver installed?

---

### Post by xTorvos on 2008-05-17
> **badfish591 said:**
> is your graphics driver installed?

How would I go about doing this?  How do I know if it is?  This is a fresh install, so would it do this automatically?  I'm not computer illiterate, but almost all linux terms are foreign to me so I basically have no idea what I'm doing.

---

### Post by overdrank on 2008-05-17
> **xTorvos said:**
> How would I go about doing this?  How do I know if it is?  This is a fresh install, so would it do this automatically?  I'm not computer illiterate, but almost all linux terms are foreign to me so I basically have no idea what I'm doing.
HI and welcome, you can start by looking under system, administration, drivers manager. There you should find you can enable your drivers for you nvidia graphics card.

---

### Post by xTorvos on 2008-05-17
> **overdrank said:**
> HI and welcome, you can start by looking under system, administration, drivers manager. There you should find you can enable your drivers for you nvidia graphics card.

On a side note, (I don't know if it makes a difference) this was found under hardware drivers.  It says "nvidia_new [x] Not in use".

---

### Post by overdrank on 2008-05-17
> **xTorvos said:**
> On a side note, (I don't know if it makes a difference) this was found under hardware drivers.  It says "nvidia_new [x] Not in use".

Ok so the box is checked to enable  but it is not in use. I would try and uncheck the box reboot the system then try and enable the driver again.

---

### Post by xTorvos on 2008-05-17
OK, I ended up doing some update things that I found in this thread.  [http://ubuntuforums.org/showthread.php?t=796794](http://ubuntuforums.org/showthread.php?t=796794)

I also installed the compizfusion config manager.  After that I went back tot he hardware acceleration driver and it was unchecked. i checked it and restarted. Now i am going to attempt to apply some of the desktop effects.  will report back later.

---

