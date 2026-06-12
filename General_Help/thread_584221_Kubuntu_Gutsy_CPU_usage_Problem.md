---
title: "Kubuntu Gutsy CPU usage Problem"
date: 2007-10-20
forum: General Help
---

### Post by steelfanatic on 2007-10-20
For some reason (I just installed Gutsy not upgrade) My CPU (Dual core) keeps staying at 30% usage (CPU1) , I opened Ksysguard  and "ksoftirqd/1" stays at about  30%. What is this? Why can't I stop the program?

---

### Post by steelfanatic on 2007-10-20
Funny, I just Uninstalled the new Kubuntu desktop search daemon, (forgot the name),
Rebooted, now CPU0 is at 30% with "ksoftirqd/0"......I'm lost here.

---

### Post by steelfanatic on 2007-10-21
Anyone with the same problem?

---

### Post by xez on 2007-10-21
I'm experiencing this issue too. Seems to be related to this bug;
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/150515](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/150515)

edit again:
Here is a more accurate bug description:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153195](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153195)

Seems to be related to kernel module for cx8800-based TV-capture cards. (in my case, a WinFast TV2000 Deluxe).

---

### Post by steelfanatic on 2007-10-22
Please post when you hear more on this.....or how to do this.

---

### Post by xez on 2007-10-23
For the record, I've just removed my Leadtek WinFast TV2000 Deluxe capture card since I never actually use it any more, and the problem has gone, Gutsy is running sweet. (I removed it prior to a reinstall, so just removing the card may not actually fix the problem unless the module is removed too. Experts...?).

Hopefully the bug in gets fixed for people who actually need this hardware functionality though!

Good luck...

---

### Post by steelfanatic on 2007-10-24
I did the same myself, but, heres the problem: I replaced it with a pvr-150, it fixed the problem (great card) theres no "easy" way to watch or {record } in Linux like windows. 
All I want to do is  watch TV and hit a red record button. MythTV, Freevo (very difficult to setup and designed for "full time" media boxes) and using Mplayer/VLC is fine but you have to use a terminal to change channels.... Oh well...maybe someday.

---

### Post by pcordas on 2007-10-24
I also use the same TV card (Leadtek WinFast TV2000) and have the same problem with 30% CPU usage all the time (process ksoftirqd). 

It looks like it's the kernel module cx8800 that's doing this. When I unload it from kernel (sudo  modprobe -r cx8800) trouble is gone and CPU usage is normal again. Unfortunately that renders my TV card useless of course.. :(  #-o

---

### Post by arthur_kalm on 2007-10-24
Hmm, I'm having the same problem and AFAIK I don't have a capture card (this is a work computer). Is there a way to shutdown that process? Or maybe blacklist the module? Thanks.

**Edit:** I tried pcordas's solution and it doesn't seem to work... it's still using around 15% CPU (as it was before). How else can I remove it?

P.S. I'm using a Pentium D computer... not sure if that changes anything (and Gutsy of course).

**Edit 2:** OK I figured it out what was causing the problem. When I launch VirtualBox to run a virtual instance of Windows, the process starts to take up a lot of CPU (20% or so). As soon as I closed VirtualBox, it went back to normal. I guess I gotta file a bug with VirtualBox then :P

---

### Post by steelfanatic on 2007-10-24
OK, kind of "fixed" my TV problem here, setup MythTV, installed Virtual box, installed MythBuntu as a guest, now I have TV in a "window" and can record when I wish! :)

---

### Post by grege on 2007-11-02
There is any easy way to watch TV, just install Kaffeine. You do not need all of KDE it will run under Gnome. It has a simple select region and scan for channels, and even a red button to record (plus timers etc). For those of us that just use the card for occassional watching programs in a window while doing something else, it is great. 

Myth TV and Freevo are only suitable for stand alone multimedia machines.

---

### Post by vankaszaner on 2007-11-09
I solved that problem last moment before I decided to get back to Feisty. 
I changed the kernel  to 2.6.22-14-383 from 2.6.22-14-generic. The installation is simple:

apt-get install linux-image-2.6.22-14-386

If you use the i.e. restricted NVIDIA driver you have to do following:

apt-get install linux-restricted-modules-2.6.22-14-386

Now I can watch my TV and when not: CPU usage is 0%!

P.S. I work on 32-bit platform. If you've got  64bit processor i.e. AMD Athlon 64 or some kind of 64bit Intel, it will possibly affect your computer performance negatively...perhaps.

Don't forget to reboot with your new kernel.

---

### Post by residentsa on 2007-11-17
> **vankaszaner said:**
> I solved that problem last moment before I decided to get back to Feisty. 
I changed the kernel  to 2.6.22-14-383 from 2.6.22-14-generic. The installation is simple:

apt-get install linux-image-2.6.22-14-386

If you use the i.e. restricted NVIDIA driver you have to do following:

apt-get install linux-restricted-modules-2.6.22-14-386

Now I can watch my TV and when not: CPU usage is 0%!

P.S. I work on 32-bit platform. If you've got  64bit processor i.e. AMD Athlon 64 or some kind of 64bit Intel, it will possibly affect your computer performance negatively...perhaps.

Don't forget to reboot with your new kernel.

I was just about to switch back to Feisty when I found this! Thanks for the fix.

---

### Post by alphaniner on 2007-12-25
Just confirming.  I have a WinFast 2000XP Expert and was plagued by the ksoftirq CPU sink.  I unloaded the associated module as suggested and that removed the process.  Not a big loss considering I never managed to get the gorram thing working.  My thanks to pcordas for this... err... :neutral: fix!

---

