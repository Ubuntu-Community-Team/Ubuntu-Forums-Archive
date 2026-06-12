---
title: "Need help reinstalling Gutsy"
date: 2007-11-12
forum: General Help
---

### Post by waldrepdebater on 2007-11-12
I'm having some major problems with ubuntu 7.10 that I'm currently dual-booting with window's vista. (see my other thread further down)  I would like to re-install gutsy to get a clean install.  Maybe this could be accomplished with running the install in rescue mode, I don't know.  How do I go about doing this?

---

### Post by taurus on 2007-11-12
Just do your normal installing except tell the installer to format the partition, giving you a clean partition.

---

### Post by waldrepdebater on 2007-11-12
Will that have any effect on the Vista partition?  I don't have the ability to re-install windows if anything goes wrong so I'm worried about risking that.

Edit: Oh, and how do I tell the installer to re-format the partition?  Is there an easy option for an extremely non-tech savvy person to click on?  I have a basic knowledge of computers and can copy-paste code into the terminal but that's about it at the moment.

---

### Post by taurus on 2007-11-12
As long as you point it to the right partition, it won't effect windows.  So, better be careful with it when you get to the partition screen.

p.s.  You want to use the manual when you get to the partition screen, [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing).  Then, you can check to have it format.

---

### Post by waldrepdebater on 2007-11-12
Which of these partitions is the one to re-format?  I can see which one is the vista, but which one holds Ubuntu?

[http://img215.imageshack.us/img215/974/partitionlv6.jpg](http://img215.imageshack.us/img215/974/partitionlv6.jpg)

---

### Post by taurus on 2007-11-12
Why don't you open a terminal, Applications -> Accessories -> Terminal, from the LiveCD and post the output of this command here.

```
sudo fdisk -l <-- Lower case letter l, not number 1.
```

---

### Post by waldrepdebater on 2007-11-12
Here it is:

```
bill@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x169876e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019     8185086   27  Unknown
/dev/sda2   *        1020        6384    43087595+   6  FAT16
/dev/sda3            7827       11217    27231191+   7  HPFS/NTFS
/dev/sda4           11218       14593    27117720    5  Extended
/dev/sda5   *       11218       14448    25952976   83  Linux
/dev/sda6           14449       14593     1164681   82  Linux swap / Solaris
bill@ubuntu:~$ 

```

---

### Post by taurus on 2007-11-12
> **waldrepdebater said:**
> Here it is:

```
bill@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x169876e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019     8185086   27  Unknown
/dev/sda2   *        1020        6384    43087595+   6  FAT16
/dev/sda3            7827       11217    27231191+   7  HPFS/NTFS
/dev/sda4           11218       14593    27117720    5  Extended
[B][COLOR="Blue"]/dev/sda5   *       11218       14448    25952976   83  Linux
/dev/sda6           14449       14593     1164681   82  Linux swap / Solaris[/COLOR][/B]
bill@ubuntu:~$ 

```

Okay, when you get to the partition screen, pick Manual and mount /dev/sda5 as / and format it and /dev/sda6 as swap.  Chances are the installer will automatically mount /dev/sda6 as swap so you may not have to do it but just in case, /dev/sda6 is your swap partition.

---

### Post by waldrepdebater on 2007-11-12
Thanks, I'll try that now.

---

