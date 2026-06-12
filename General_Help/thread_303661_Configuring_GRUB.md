---
title: "Configuring GRUB"
date: 2006-11-20
forum: General Help
---

### Post by Emos on 2006-11-20
Hello,
I've just installed Ubuntu 6.10 on my hda, and after that I inserted another HD in my case that is now recognised by Linux as hdb. On this hdb I had previously installed Windows XP, and I'd like to configure GRUB to allow me to choose which system to use at every boot.
I tried to add 
> title           Windows XP Media Center Edition
root            (hd1,1)
savedefault
makeactive
chainloader     +1
in menu.lst but it didn't work out...

Please help!
Thanks

Emanuele

---

### Post by Emos on 2006-11-20
Sorry, I forgot to tell you that in the HD that contains Windows there are 3 partitions, and linux recognises the one that contains WinXP as hdb6.
So i tried in grub (hd1,0) and it tells me "starting up..." but it doesn't, then I tried (hd1,5) and it tells me "Error 12: invalid device requested".

What can I do?

Thanks

---

### Post by Emos on 2006-11-21
Please help!
I tried all the possible combinations from hd1,0 to hd1,6 and noone worked... Only when triyng to boot the hd1,0 it appears "starting up..." but then nothing happens...

---

### Post by djlyx on 2006-11-21
Im new at this, but perhaps you can try to re-install ubuntu altogether.  It might automatically configure grub and give you the option to either use ubuntu or xp during boot up.

---

### Post by Emos on 2006-11-21
Is this the only option? :confused: :(

---

### Post by vidak on 2006-11-21
> **Emos said:**
> Is this the only option? :confused: :(

Of course not. Do you have a working version of menu.lst? The first thing to do would be to restore it. Then reboot, and when grub comes up, there is a possibility to get a command line. I don't remember very well, but you should press 'e' or something else (it's written somewhere under the option list). Then entering 'help' gives you the usable commands in grub. Don't forget about the command-line completion (if you press Tab, like in bash...)
This is a good way to explore the parameters for the root option eg. You have to enter 
root (hdTAB
you get a list of the drives, and choose a drive, eg. hd0
root (hd0,TAB
list of partitions, choose one, eg. 1
root (hd0,1)

Just remain calm, don't panic, and explore the features of grub...

Here is the corresponding part of my menu.lst
```

title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

with the output of sudo fdisk -l

```

/dev/hda1   *           1        1305    10482381    c  W95 FAT32 (LBA)
/dev/hda2            1306        1436     1052257+  82  Linux swap / Solaris
/dev/hda3            1437        2611     9438187+  83  Linux
/dev/hda4            2612        9729    57175335   83  Linux

```

Did this help you?

---

### Post by Emos on 2006-11-22
Thank you, I tried this, and this is my fdisk -l:
```
Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9587    77007546   83  Linux
/dev/hda2            9588        9964     3028252+   5  Extended
/dev/hda5            9588        9964     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1147     9213246    c  W95 FAT32 (LBA)
/dev/hdb2            1148        9731    68950980    f  W95 Ext'd (LBA)
/dev/hdb5            1148        4971    30716248+   e  W95 FAT16 (LBA)
/dev/hdb6            4972        9731    38234668+   7  HPFS/NTFS

```
I tried your 
```
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```
putting (hd1,0) and (hd1,1) to (hd0,7) instead of (hd0,0), but with no success... :(

---

### Post by vidak on 2006-11-22
Did you try to check out the needed options using grub's command-line completion features mentioned in the previous post? You could try to get a grub command line, and probe different options of root. Looking at the output of fdisk, the first part should be hd1. But I'm not sure about the second (the partition) part I got confused of the large number of Window$-partitions... :)
Tell me please if you manage to solve the problem...

---

### Post by Emos on 2006-11-23
I tried that. I found out the right drive is hd1, and the possible partitions are 0, 4, 5. But Id doesn't start! With partition 4 and 5 it tells me "wrong device"...

---

