---
title: "Mounting mac osX hard drive"
date: 2005-04-05
forum: General Help
---

### Post by fallenone on 2005-04-05
hi there i seem to be having some trouble mounting the mac harddrive rom ubuntu live cd, i've been using:

mount -t hfsplus /dev/hda/ /mnt/macosX

but i seem to be getting errors such as bad super block and i've tried other drives also such as hda1 hda2 and some thing just wondering if im doing something wrong or? if you could please point in teh right direction this is a friend of  mines g4 powerbook and needs some files off of it, it seems that the os crashed or something, but the hd still checks out fine, ran disk utitlies on it any help would be much appreciated!

---

### Post by jdonnell on 2005-04-27
I'm having the same problem. Please post your solution if you found one.

---

### Post by tormod on 2005-04-28
[QUOTE=fallenone]hi there i seem to be having some trouble mounting the mac harddrive rom ubuntu live cd, i've been using:

mount -t hfsplus /dev/hda/ /mnt/macosX[/QUOTE]
On Mac-formatted disks, partitions 1-5 are often system and driver partitions. The first "useful" partition is often /dev/hda6

You can use /sbin/parted to list the partitions on the drive, that will help you to find if it's /dev/hda6 or /dev/hda7 etc.

---

