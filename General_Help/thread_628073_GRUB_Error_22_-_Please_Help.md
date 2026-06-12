---
title: "GRUB Error 22 - Please Help"
date: 2007-11-30
forum: General Help
---

### Post by Enishiru on 2007-11-30
I've been using Ubuntu for a few months, and I recently upgraded to 7.10 without any problems.

However, my friend recommended Kubuntu, so I installed that as well.

On my laptop I had Windows XP, Ubuntu 7.10, and Kubuntu 7.10.

However, after trying it out, I decided to get rid of Kubuntu. I asked my friend how, and he said "delete the partition".

Now, I followed his advice, and when I start my computer, I get an error like this:

Loading GRUB...

Error 22

(close enough)

So, I'm assuming I deleted important files for GRUB that were in the Kubuntu partition?

However, I still have Ubuntu installed. Is there any way I could modify the files on Ubuntu to get GRUB working again?

I can access all my files because I'm running a live cd of Ubuntu 7.10 right now.

Any help is appreciated.

---

### Post by teryowen on 2007-11-30
boot from live CD

then go to terminal and type

sudo fdisk -l
cat /media/sda2/boot/grub/menu.lst     --> or whereever ur ubuntu is mounted

copy and paste out put

---

### Post by panda726 on 2007-12-04
I am having about this same problem.  I fixed error #22 by on grub loading, editing the boot command for a normal boot.  Change the line ```
Root  (hd0,0)
``` (or whatever the correct drive/partition is) to ```
root  (**s**d0,0)
```

Now I am getting error #23.  Any help would be appreciated.

---

### Post by teryowen on 2007-12-04
it should remain hd0 even if the hard drive is sda....

boot of a live CD

and post output of:

sudo fdisk -l

---

### Post by panda726 on 2007-12-04
Here it is.  Windows is on sdc1, and kubuntu is on sdc2.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2578748

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4111    33021576    c  W95 FAT32 (LBA)
/dev/sda2            4112        4870     6096667+   b  W95 FAT32

Disk /dev/sdb: 13.0 GB, 13020069888 bytes
255 heads, 63 sectors/track, 1582 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x26717586

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1582    12707383+   6  FAT16

Disk /dev/sdc: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1567    12586896    7  HPFS/NTFS
/dev/sdc2            1568        3559    16000740   83  Linux
/dev/sdc3            3560       19452   127660522+   5  Extended
/dev/sdc5            3560        4057     4000153+  82  Linux swap / Solaris
/dev/sdc6            4058        6042    15944481   83  Linux
/dev/sdc7            6043       14397    67111506    b  W95 FAT32
/dev/sdc8           14398       16925    20306128+   b  W95 FAT32
/dev/sdc9           16926       19452    20298096    b  W95 FAT32

```

I really would like to get kubuntu booting shortly.  Windows can wait, as I almost never boot it.

Thanks,

Tor

---

### Post by panda726 on 2007-12-04
Solved for me.  Correct drive was hd0,2, while kubuntu has the drives in a different order, such that linux is on sdc2.  Thank you Tery and to whoever in some other thread pointed someone to a grub error and solution page the combination of which got me booted.

Tor

---

### Post by tech9 on 2007-12-04
repair with super grub disk...

---

### Post by teryowen on 2007-12-04
Good to hear it was solved, sorry i couldnt help i was at school, and still am...

---

### Post by panda726 on 2007-12-04
Actually, if I had known, I had opened the page which linked me to the solution howto before I posted.  The solution staring me in the face, and I had only to realize it was there.  Windows also should boot, except that I don't have enough reason to boot it to be worth hibernating or rebooting to find out.  As I have heard someone say, "The only reason to run windows is because you absolutely must run a program that you cannot get to run any other way."

Tor

---

