---
title: "Access NTFS drive"
date: 2007-03-17
forum: General Help
---

### Post by The Anomaly on 2007-03-17
Greetings,


I'm sure this is a common question, but I have an extra problem added to it. Let me begin with my system set up. I have two 250 gig drives. The first one is my Windows drive, and it has two partitions. The other 250 gig drive is running Ubuntu. I have all my files on the windows drive (running NTFS) and I need to access them from Ubuntu. From what I've read...I could have gotten them to be mounted from when I was installing Ubuntu. However, when it asked about the drives, I totally excluded any drive that seemed like it was running windows....I was too paranoid about maybe losing my data (I really didn't know what I was doing). The "Ubuntu Guide" said something about going to System --> Administration --> Drives, but I couldn't find that option on the list...

Anyway, I have a 250 gig drive, with two partitions with an NTFS filesystem. I did not tell Ubuntu to mount these from the beginning...and now I can't access them.

I'm running Edgy Eft if you need to know.

---

### Post by s1ptome on 2007-03-17
hi,

you may follow this guide instead, to have your windows partition mounted at each boot:
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html")

modify your /etc/fstab, then you can mount your disk with "sudo mount -a" rather than a reboot.

if you don't want the disk to be mounted at boot, replace "umask=0222" with "noauto,umask=0222"

Oh, and whatever you try, remember to make a copy of this file before!

bye,
s1ptome

---

### Post by chewearn on 2007-03-17
The default ubuntu can only read from a ntfs partition.

Here is the guide to install ntfs-3g, if you want to be able to write to ntfs partition:
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

