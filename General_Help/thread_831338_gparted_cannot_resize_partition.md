---
title: "gparted cannot resize partition"
date: 2008-06-16
forum: General Help
---

### Post by blampars on 2008-06-16
I wanted to resize my partition so that I could re-install windows xp and have a dual boot system.  I miss my computer games and am tired of trying to get them to work in linux.

the resize failed, here is the gparted_details.htm
[http://tricky.bluesphereweb.com/gparted_details.htm](http://tricky.bluesphereweb.com/gparted_details.htm)

can anyone tell me what exactly happened/went wrong please?

thanks,
-b

---

### Post by blampars on 2008-06-30
pretty please? :)

---

### Post by sailor2001 on 2008-06-30
I would suggest using xp to resize your partition.......rt.click "mycomputer" and I think it's "manage" "hard drive"   don't have xp so can't tell you exact language.

---

### Post by VMC on 2008-06-30
Is that link your link or someone else's problem?
At any case here is a better way of re-sizing using gparted:
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

From a Terminal type this:

```
sudo fdisk -l
```

come back with the details

---

### Post by blampars on 2008-06-30
that link is my specific problem

here's my output from 'sudo fdisk -l'
```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7108    57094978+  83  Linux
/dev/sda2            7109        7296     1510110    5  Extended
/dev/sda5            7109        7296     1510078+  82  Linux swap / Solaris

```

also, i used the same procedures to try to resize my partition as stated in the above link

-brad

---

### Post by blampars on 2008-07-05
anyone have any other ideas?

---

