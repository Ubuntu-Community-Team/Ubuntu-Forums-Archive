---
title: "Cannot boot Ubuntu 7.10"
date: 2007-11-25
forum: General Help
---

### Post by Graham1 on 2007-11-25
Hi

Since re-creating (formating) my partitions (sda5 and sda7), I am no longer able to boot into Ubuntu 7.10. The same also occurs for Fedora 8. Strangely, openSUSE 10.3 wasn't affected by this. My setup is as follows:-

sda1: Ubuntu 7.10
sda2: openSUSE 10.3
sda3: Fedora 8
sda4: Extended
**sda5:    fat32 (XOSL Boot Loader)**
sda6:    Linus swap
**sda7:    Shared Data**

Why would this cause Ubuntu and Fedora to no longer boot? Btw, grub is installed on each Distro's partition. XOSL is used to boot to these partitions. Can my Ubuntu partition be fixed or am I looking at doing a re-install? 

:)

Edit: Btw, I re-installed XOSL to sda5 and that was when I came across this problem :(.

---

### Post by Sendervictorius on 2007-11-26
How far do you get when you "cannot boot" - ? Does it start the grub menu? If not I suggest you have reset the MBR, and you should reinstall grub (e.g. from a live CD).

---

### Post by Graham1 on 2007-11-26
It did start the GRUB menu a couple of times which then displayed mounting errors (sorry, can't remember the exact message). Now, all I am getting is a flashing white cursor in the top left corner :(.

:)

---

### Post by Sef on 2007-11-26
Have you tried using [Super GRUB Boot Loader]("http://supergrub.forjamari.linex.org/")?  It will reinstall GRUB.

---

### Post by Graham1 on 2007-11-26
> **Sef said:**
> Have you tried using [Super GRUB Boot Loader]("http://supergrub.forjamari.linex.org/")?  It will reinstall GRUB.

I haven't. Will this touch my other partitions? Would I be able to install from openSUSE (sda2) to sda1? (Ubuntu partition). What I don't understand is why these partitions (Ubuntu and Federa) were affected by deleting and re-creating these partitions (same size, filesystem, etc). 

:)

---

### Post by Graham1 on 2007-11-26
Ubuntu 7.10 and Fedora 8 are now re-installed :D. I'm still curious as to why these partitions were affected, Anyone have any ideas?

:)

---

