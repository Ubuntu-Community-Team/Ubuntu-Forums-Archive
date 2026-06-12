---
title: "Has anyone installed Maya 8.0 unlimited from download???"
date: 2006-09-05
forum: General Help
---

### Post by Tashamon on 2006-09-05
I need a walkthrough on how to install Maya 8.0 unlimited on ubuntu.  There are only vague instructions in package and I can only find Win and OS/X walkthroughs via google.  If anyone has installed this program specifically please enlighten me.

---

### Post by taurus on 2006-09-05
Did you download a .tar, .bin, or .sh?

---

### Post by Tashamon on 2006-09-06
its .iso but I've extracted it to .rpm packages

---

### Post by leif3d on 2006-09-22
> **Tashamon said:**
> its .iso but I've extracted it to .rpm packages

I'm going to install Maya 8 x64 on Ubuntu amd64 next week when I get my license from Autodesk, so any help on this issue would be appreciated. I previously read the install guide for Maya 7 on Ubuntu, but it didn't say if it was a 32 bit ubuntu OS or 64 bit and if maya 8 would work. Thanks!;)

---

### Post by leif3d on 2006-09-28
UPDATE!: I installed Maya 8 64bit on Ubuntu 64bit by converting it to .deb with Alien and then running dpkg...I followed some steps on a previous post and everything works fine. EXEPT! Maya runs slower on linux than on WinXP x64. The Shaded view is about a 10% slower and Textured view is 50% slower!...I installed the latest Nvidia drivers fine...everything seems very snappy compared to windows exept that viewport performance issue, is anyone else having the same problem? I've heard about XGL and Compiz, do these things help OenGL performance in any way? is there something that does help? Please help!

---

### Post by v8YKxgHe on 2006-10-08
Hey,

got a guide for installing Maya 8 on 32bit Linux? I tried converting it to .deb files and installed them, but Maya is no where to be seen on my Ubuntu install. Even typing "maya" at terminal says "command not found"

Any Ideas?

---

### Post by ooZAFLE on 2006-10-31
I got mine installed no problem but after installing the license file it exits saying that it installed fine, but reloads the license installer right after exit instead of loading maya. i've never got maya to run past that step. any ideas? doesn't verbose any errors either, and permissions are fine... err

edgy x86, beryl

---

### Post by iyeo on 2006-11-08
You need to convert rpm to debs with alien.  More details here:
[http://ubuntuforums.org/showthread.php?t=66859&highlight=maya](http://ubuntuforums.org/showthread.php?t=66859&highlight=maya)

I have Edgy x64 running Maya64 but need to fix the fonts.

---

### Post by iyeo on 2006-11-08
You need to convert rpm to debs with alien.  More details here:
[http://ubuntuforums.org/showthread.php?t=66859&highlight=maya](http://ubuntuforums.org/showthread.php?t=66859&highlight=maya)

I have Edgy x64 running Maya8_64 but need to fix the fonts.

---

### Post by zyml on 2006-11-28
Install csh:

sudo apt-get install csh

Then go into Maya directory:

cd /usr/aw/maya8.0/bin
./Maya8.0

---

### Post by veeraa on 2007-12-03
I've helped a frind install both maya 8.5 and Maya 2008 on Ubuntu 7.04 and 7.10 in 32-bit and 64-bit configurations. It was a breeze and yeah with nvidia cards, thing s are much better interms of uability and performance. I can put up a guide if anyone needs help.

---

