---
title: "Making a live cd from Ubuntu distribution..."
date: 2004-11-15
forum: General Help
---

### Post by spaguzz on 2004-11-15
I'd like to make a livecd from a preinstalled Ubuntu distribution, i found  some scripts to meke it easy. But also these ones need some reference! I red to use them i need a kernel compiled with "ovlfs-devfs". My questions are simple:

1) in ubuntu kernel there are this "extensions"?

2) someone got an idea how to make a livecd easy? this is my final universitary-stage, can you help me?

Thanks a lot..

---

### Post by spaguzz on 2004-11-16
Can someone tell me if Ubuntu kernel 2.6.* "ovlfs" and "devfs" are already compiled ? I need them to use Live Script.

If not, can I use a specific kernel, like "kernel-2.4.26-ovlfs-devfs-alsa-1.0.4-i486-1.tgz"?

---

### Post by wanderer on 2004-11-17
[QUOTE=spaguzz]Can someone tell me if Ubuntu kernel 2.6.* "ovlfs" and "devfs" are already compiled ? I need them to use Live Script.

If not, can I use a specific kernel, like "kernel-2.4.26-ovlfs-devfs-alsa-1.0.4-i486-1.tgz"?[/QUOTE]


ovlfs doesn't work in kernel 2.6.x, as far as I know.

also, for Gnome's 2.8.x HAL to work, you need kernel 2.6.x, otherwise, plug and play in Gnome won't work at all.

Here's another way to make a live cd distro.  Based on the instructions of LormaLinux live cd, but can be applied here. 

[http://linux.lorma.edu/forum/viewtopic.php?t=372](http://linux.lorma.edu/forum/viewtopic.php?t=372)

---

### Post by sb73542 on 2004-11-18
[http://developer.berlios.de/projects/livecd/](http://developer.berlios.de/projects/livecd/)

This is supposed to work with 2.6.x.  PCLOS uses this.

---

