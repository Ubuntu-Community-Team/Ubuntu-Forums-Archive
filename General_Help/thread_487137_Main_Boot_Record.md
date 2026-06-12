---
title: "Main Boot Record"
date: 2007-06-28
forum: General Help
---

### Post by phanteh on 2007-06-28
Hi all,

I suppose you could call me a windows power user or w/e but recently I've been swayed by linux, mostly because I know a good thing when I see it!

But recently I've run into a problem - I'm often sorting out peoples computers for them after they riddle them with viruses etc. and often the easiest way to go about it is to attach their primary HD to my machine and blitz it from there / copy drivers needed etc. etc. Unfortunately, every time I attach a HD (in place of my CD drive - IDE only so far...) GRUB decides that it can't find the Ubuntu 7 installation, or my windows installation. Quite annoying!


Anyway, I slapped in the XP installation CD and reinstated the windows MBR - I was just wondering if it's possible to boot into linux using the windows boot loader rather than GRUB, how this effects kernel updates (i.e. would I have to manually edit the MBR record when I update the kernel) or is it possible to stop GRUB from fannying around when I attach another HD?

Many Thanks for any help!


p.s. 
Hope this is the right area of the forum - couldn't decided where it belonged!

---

### Post by louieb on 2007-06-28
[Booting Using NTloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=351692")
By choice I use GRUB but it does have it limits. Like sometimes getting lost when you hardware configuration changes.

---

### Post by Brucevdk on 2007-06-28
EDIT: aww chucks a second too late,the post referenced above basically states the same thing as I do here below.

> **phanteh said:**
> I was just wondering if it's possible to boot into linux using the windows boot loader rather than GRUB,

Yes this is possible. See [NT OS Loader + Linux mini-HOWTO: The Linux part of the work]("http://tldp.org/HOWTO/Linux+NT-Loader-5.html"). Here's what you'll have to do:

1) Install GRUB not on the MBR (Master Boot Record) but the root (/) partition.

2) Use the following command to dump the first 512 bytes to a file named ubuntu.bin:
```

dd if=/dev/sda2 of=/tmp/ubuntu.bin bs=512 count=1
```
Where *sda2* is the your root partition, see *sudo fdisk -l* .

3) Move this file to the root of the filesystem on which Microsoft Windows is installed (e.g. C:\) and modify the NT Loader's configuration file (boot.ini) to include the following line:
```

C:\ubuntu.bin="Ubuntu GNU/Linux"
```

> **phanteh said:**
> how this effects kernel updates (i.e. would I have to manually edit the MBR record when I update the kernel)

All the procedure above does is boot from the NT Loader on the MBR to GRUB on the root partition, basically GRUB will behave as usual.

---

