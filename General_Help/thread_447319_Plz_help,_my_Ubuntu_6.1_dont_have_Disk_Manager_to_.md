---
title: "Plz help, my Ubuntu 6.1 dont have Disk Manager to mount partition"
date: 2007-05-17
forum: General Help
---

### Post by mocqueanh on 2007-05-17
I installed Ubuntu 6.1 for studying ( not for use now because i'm a newbie, so my partition for Ubuntu just 9.7 GB ).

And i'm reading some book course for Ubuntu. It introduce me mount Windows partition in Ubuntu by open System>Administration>Disk.

But (i dont know why) in my Ubuntu menu, the System>Administration doesnt have the Disk line to open Disk Manager.

I tried to using command line to mount Windows partition, but nothing happen, i dont see Windows files in /mnt/windows.

I have 3 partition of Windows: C ( Win XP), D(Multimedia) and E (SETUP). All both are FAT32 file system.

And when i use Disk Analyzer in Ubuntu, it doesnt see my Windows partition.
(I tested my Ubuntu CD intergrity, and test succesfully.)

Here are 3 pics that i take from my screen.

[IMG]http://uploadaz.com/uploadaz/I05/1179459326.jpg[/IMG]


[IMG]http://uploadaz.com/uploadaz/I05/1179456253.png[/IMG]

[IMG]http://uploadaz.com/uploadaz/I05/1179457407.png[/IMG]

---

### Post by thelinuxguy on 2007-05-18
I can't tell you about Disk Manager but this may help
[http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy) (section 1.15)
and this
[http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/](http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/)

---

### Post by mocqueanh on 2007-05-21
OK, after i use the shell:
sudo fdisk -l
I can see all my partition and can mount it.
But new things i dont understand.
What is hdb, hda, sda in the /dev
In my PC, i only see: hdb, hdb1,hdb2,... in /dev
But some tutorials on Internet, it say: mount sda, hda. What does the mean ?

And after use fdisk -l  Ubuntu appear 6 partition:
hdb1: FAT32
hdb2: Linux Extend
hdb3 : Linux (Solaris)
hdb5: FAT32
hdb6: FAT32
hdb7: Linux swap

I think when install Liux, it only create 2 partition: one for install and one for swap ? So why here are 3 Linux partition ? ( in my Windows XP, i just see 5 partition )
And where is hdb4 ?
And i cant mount the hdb2 and hdb 7, Ubuntu say: arent you trying to mount extend partition? And: this is swap, no need to mount.

All otheres partition, i can mount fine.

---

### Post by thelinuxguy on 2007-05-22
> **mocqueanh said:**
> What is hdb, hda, sda in the /dev
Your IDE disks will be named hda (Primary Master), hdb (Primary Slave), hdc (Secondary Master), hdd (Secondary Slave). Your SATA disks (as well as USB drives) will be named as sda and so on. However, you may want to read this: [http://www.nabble.com/HDA-vs.-SDA-kernel-changes--tf3704214.html#a10358874](http://www.nabble.com/HDA-vs.-SDA-kernel-changes--tf3704214.html#a10358874), which indicates that things may have changed with recent kernels.

> 
In my PC, i only see: hdb, hdb1,hdb2,... in /dev
But some tutorials on Internet, it say: mount sda, hda. What does the mean ?

You will only see those files for which you have the hardware. Your IDE disk is connected as the Primary slave. Hence you see only hdb. hdb1 is the first partition on that drive and so on. The tutorials expect you to replace sda, hda with the correct one for your system. (With older systems, you could also see files in /dev for which the hardware was not connected.)

> 
And i cant mount the hdb2 and hdb 7, Ubuntu say: arent you trying to mount extend partition? And: this is swap, no need to mount.


hdb2 is an extended partition. It contains logical partitions. You can mount the logical partitions which are in the extended one but not the extended partition itself. The SWAP partition is used for virtual memory purposes by Linux. It is not to be mounted as you cannot store your data on that partition.

> 
I think when install Liux, it only create 2 partition: one for install and one for swap ? So why here are 3 Linux partition ? ( in my Windows XP, i just see 5 partition )
And where is hdb4 ?

[COLOR="Blue"]Can't answer this one as I have come across Windows extended partitions so far. Someone more knowledgeable could answer this and the partition layout you have. BTW, where did you get the Solaris partition from?[/COLOR]

---

### Post by mocqueanh on 2007-05-29
Thank for answer, here is my partition table after use fdisk -l:

```

Disk /dev/hdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2882    23149633+   c  W95 FAT32 (LBA)
/dev/hdb2            2883        8467    44861512+   f  W95 Ext'd (LBA)
/dev/hdb3            8468        9733    10169145   83  Linux
/dev/hdb5            2883        6475    28860741    b  W95 FAT32
/dev/hdb6            6476        8408    15526791    b  W95 FAT32
/dev/hdb7            8409        8467      473886   82  Linux swap / Solaris


```

---

