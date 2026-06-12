---
title: "Problem booting windows after changing partition"
date: 2007-03-29
forum: General Help
---

### Post by Sauron.SS on 2007-03-29
Hi all,
a friend of mine installed Ubuntu after windows and he had a configuration like this:

/dev/sda1 Windows NTFS
/dev/sda2 Ubuntu /
/dev/sda3 Ubuntu swap
/dev/sda4 Ubuntu /home

now, with partition magic he changed the ntfs partition and splitted into 3 partition, now it look like this:

/dev/sda5 windows vfat
/dev/sda6 windowf ntfs (this is the partitino to boot)
/dev/sda7 windows vfat (for sharing files etc)
/dev/sda2 ubuntu /
/dev/sda3 ubuntu swap
/dev/sda4 ubuntu /home

Well, ubuntu is still working but but i can't figure out how to boot windows
in menu.lst the windows entry looked like this:
------
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
------

Now i don't know what to put in the root line instead (hd0,0)
i thought i had to set the root partition to (hd0,5) but it didn't work, i tryed all from 0 to 6 :P
nothing works (well hd0,1 is ubuntu root so ofc it doesn't work)
If i try (hd0,5) or whatever it is i get error 12 from grub

i don't know what i'm missing, i've alwais installed windows in the first primary partition so i don't know exactly what to do now, i can mount the win partition from ubuntu anyway, so the hard disk is working correctly....

help me ^^

---

### Post by JohnPhys on 2007-03-29
When you changed the partitions in partition magic, did you make sure to set the partition as bootable?

---

### Post by Sauron.SS on 2007-03-30
i set it bootable using cfdisk

reading around on the net i see that windows need to be in a primary partition, this is probably the problem, and if it's true i don't think there's much to do :(

---

