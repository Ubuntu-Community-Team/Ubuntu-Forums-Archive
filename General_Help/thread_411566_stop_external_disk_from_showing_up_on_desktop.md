---
title: "stop external disk from showing up on desktop"
date: 2007-04-17
forum: General Help
---

### Post by notatoad on 2007-04-17
is there a way to stop only my external hard disk from showing up on the desktop?  i still want it to automount when i plug it in, and i want usb keys and my mp3 player to show on the desktop.

---

### Post by dfreer on 2007-04-17
create a fstab entry for it and tell it to mount somewhere other than /media.
a good place to mount it is /mnt but it's up to you

---

### Post by notatoad on 2007-04-17
okay, i tried adding this to the end of /etc/fstab
```
/dev/sdc1   /home/kyle/externaldisk vfat defaults, locale=EN_CA.UTF8  0  0
```
and on "sudo mount -a" i got this error>  wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
 

trying fat32 for fs type gave me a different error saying "did you mean vfat", and auto gives the same error.  what did i wrong?

---

### Post by orb9220 on 2007-04-17
>  /home/kyle/externaldisk

Did you make a folder called externaldisk in your  /home/kyle/ ?

---

### Post by dfreer on 2007-04-17
> /dev/sdc1   /home/kyle/externaldisk vfat defaults, locale=EN_CA.UTF8  0  0

Try taking out the space between defaults, and locale...
so like this:

```
/dev/sdc1   /home/kyle/externaldisk vfat defaults,locale=EN_CA.UTF8  0  0
```
Also, make sure to create the folder /home/kyle/externaldisk like above poster states.

EDIT: If it still gives you a error post the results from:
```
dmesg | tail
```

---

### Post by notatoad on 2007-04-18
okay, today i booted into my ubuntu and my disk didn't mount automatically, so i opened gparted to see if it was recognized, and it was, so i clicked to mount the partition, and it mounted no problem in my home folder.  the icon still shows on the desktop though, and it has added an icon for my second internal hard disk.  i think i'm just going to give up and ignore the disk icons.  thanks for your help anyways, everybody.

---

