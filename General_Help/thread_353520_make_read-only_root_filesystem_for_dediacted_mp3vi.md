---
title: "make read-only root filesystem for dediacted mp3/video box"
date: 2007-02-04
forum: General Help
---

### Post by nytfox on 2007-02-04
I have ubuntu server installed and customized for dedicated for mp3 and vcd/dvd player. and wonder if I can make the root filesystem readonly so that the root filesystem won't get corrupted in case of power failure or I can simply unplug the pc when I want to turn it off, similar to Livecd.  I don't what the livecd approach because it is difficult to update files when you what it to upgrade or change some files.
do you have links or howto on howto making root filesystem readonly?

my ubuntu only have the basic install needed to play mp3 and VCD/DVD.
thanks

---

### Post by dcstar on 2007-02-04
> **nytfox said:**
> I have ubuntu server installed and customized for dedicated for mp3 and vcd/dvd player. and wonder if I can make the root filesystem readonly so that the root filesystem won't get corrupted in case of power failure or I can simply unplug the pc when I want to turn it off, similar to Livecd.  I don't what the livecd approach because it is difficult to update files when you what it to upgrade or change some files.
do you have links or howto on howto making root filesystem readonly?

my ubuntu only have the basic install needed to play mp3 and VCD/DVD.
thanks

Have you tried altering your GRUB boot string to load up in RO mode?

---

### Post by nytfox on 2007-02-05
yes my grub already have root=/dev/hda1 ro
but It still have no effect...

---

### Post by kitman420 on 2007-02-26
You have to edit your /etc/fstab file and make it ro instead of rw. If you're unfamiliar with fstab, do a quick google search.

---

