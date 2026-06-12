---
title: "no swap partition in ubuntu 14.04 4bit?"
date: 2017-06-17
forum: General Help
---

### Post by ubto66 on 2017-06-17
ubuntu 14.04 64bit

I have installed ubuntu 14.04 64bit on a 16gb usb memory stick. After installing additional programs, free space gets to low.

System monitor says, swap not available. If you install ubuntu 14.04 64bit and select full hdd encryption, there is no swap?

Thanks.

---

### Post by Impavidus on 2017-06-17
Using full encryption, you should have an encrypted swap partition. Or, from 17.04 on, a swap file. Unless you choose otherwise.

But I don't see the connection between installing additional programs (taking disk space), low free space and needing swap (because insufficient ram). New computers have so much ram that you don't really need swap, other than that it gives a more graceful crash in the very unlikely case you still run out of memory or if you want to hibernate.

---

### Post by oldfred on 2017-06-17
Do not know LVM nor full drive encruyption which uses it.

But if you did full drive encryption it used LVM which is Logical Volume Management inside the standard physical partitions.

 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM) 

If you just did a default install and have lots of RAM, it may have made a large swap partition inside your LVM. Generally you do not need a large swap unless hibernating and hibernating normally not recommended.

---

### Post by efflandt on 2017-06-17
How much RAM do you have and are you running short of memory to run programs, or drive space?

With my 8 GB desktop PC I do not set up swap, since it can boot as fast as it wakes from suspend, so I do not suspend and have no need to hibernate. Even on a 10.1" tablet PC with only 2 GB RAM I do not use swap because its 32 GB SSD with Win7 Pro does not have room for Linux, which I boot from SD card, and it is probably not wise to use SD or USB memory stick for swap (flash memory has limited write cycles). But I do not use that tablet PC for anything demanding because it only has 2 core 1 GHz CPU less capable than my Android phone (8 core 1.5 GHz).

What output do you get in a terminal for: df -h

Did you actually "install" Ubuntu to that 16 GB memory stick, or is that a live/install system?

---

### Post by ubto66 on 2017-06-21
Thank you. 

Computer has 4gb ram. If there is a swap sized about 4gb, I want to size the swap down to 500mb if it can be done. That would add several gbs of free space. Enough to make the system work.

---

