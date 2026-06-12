---
title: "Add an other WinOS to Win7 &amp; ubuntu (Triple boot)!!!"
date: 2013-06-18
forum: General Help
---

### Post by faissalman on 2013-06-18
Hello everyone,
i have a laptop with 5 HDD partitions:


[LIST=1]
[*]300Mio that needs windows to put some files!!
[*] 200Gio in wich is installed windows 7 64bit
[*]58  Gio empty
[*]2    Gio For the "swap"
[*] 38  Gio in wich i installed ubuntu 12.04 LTS 32bit
[/LIST]

I want to install a new windows 7 or 8 in the free 58Gio partition, any advice on how that is possible and if it is, what's the steps i should follow?

Thanks and have a nice day :)

---

### Post by zombifier25 on 2013-06-18
You said you want to install a new Windows. If so, things are going to be pretty difficult for you, because 
1. A hard drive can only contain 4 primary partitions (the free space does not count). If you want more partitions you have to remove one partition and create an extended one in its place, in which you can put as many partitions as you want.
2. Windows can only be installed on a primary partition.

So, if you want to keep Ubuntu intact, you can delete the swap partition and create a new primary partition using the free space, on which to put Windows 8. But this means you cannot use swap and you can no longer create more partitions. If you want to create an extended partition AND install a new Windows, you must delete Ubuntu or partition #1 (can you elaborate on what it does? Since I don't know if you could delete it), create a new extended partition, put new partitions inside it for Ubuntu and its swap.

To backup your Ubuntu system, use something like [Clonezilla](http://clonezilla.org/).
Also note that when Windows is installed, it will overwrite GRUB with its own bootloader, which only boots to Windows. To restore GRUB, use a Ubuntu liveCD/USB and use [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by faissalman on 2013-06-18
so what if i delete ubuntu in install the second windows first on that free space, then install ubuntu will that works fine?? if that so, can i install an other windows 7 alongside the old one normally??

---

### Post by kurt18947 on 2013-06-18
There *is* a way to have more than 4 primary partitions on an 'MSDOS' formatted disk though I'm using proprietary software to accomplish it.  
[http://www.terabyteunlimited.com/bootit-bare-metal.htm](http://www.terabyteunlimited.com/bootit-bare-metal.htm)
It'll support something like 100 primary partitions.  UEFI/GPT supports >4 partitions 'out of the box'.  I originally bought this to run multiple Windows installs before I knew about Linux/Ubuntu.  The downside to using this is once you go beyond 4 partitions, you cannot use other software for disk partitioning.  There is also one big thing to look out for when installing new O.S.s - make sure GRUB/LiLo goes in the partition, not in the disk's root.

---

### Post by oldfred on 2013-06-18
Best to install Windows in the primary partitions and have Ubuntu in logical partitions.
But second installs of Windows will install to logical partitions, but all boot files will be in the first install in the primary partition.

Vista, but applies to all BIOS/MBR installs.
 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by faissalman on 2013-06-18
[SIZE=3]thanks guys, i've learned a lot of informations but it's a little bit defficult to me to do, so i think i'll do the following:

 [/SIZE]
[LIST=1]
[*][SIZE=3]use remastersys to create a copy of my ubuntu
[/SIZE]
[*][SIZE=3]boot up with  windows 7 CD/USB installation
[/SIZE]
[*][SIZE=3]delete the 58Gio, ubuntu and swap  partitions
[/SIZE]
[*][SIZE=3]create a new partition with 60Gio and install windows 7 on  it. so i' have different windows 7
[/SIZE]
[*][SIZE=3]after that i'll install my saved  copy of ubuntu
[/SIZE]
[/LIST]
[SIZE=3]
**will that works fine?**[/SIZE]

---

### Post by zombifier25 on 2013-06-19
Kinda it. The fourth partition will be an extended partition that can contain both Ubuntu and its swap.
It also helps to look at the link oldfred provided, for more examples of successful installations.

---

