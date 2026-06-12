---
title: "I cannot see my home partition"
date: 2013-11-17
forum: General Help
---

### Post by eon01 on 2013-11-17
[IMG]http://i.imgur.com/txgrdSel.jpg[/IMG]

I was using a live distro to install it when I discovered that I cannot access my home partition and that the installation manager gave just the possibility to install the os on one partition . Normally, I have another logical partition which is my home .  
Now I am running ubuntu rescue remix and the photo is the fdisk -l output . 
Can you see what is the problem ?

---

### Post by oldfred on 2013-11-17
Please copy code from terminal and if longer post inside code tags. You can easily add code tags by using advanced editor and highlight code and click on # icon in edit panel at top.

You are only showing one large partition and swap inside an extended partition.

Does deeper search in testdisk show more old partitions. It may find multiple versions or overlapping older partitions and only some choices of recovery that do not overlap will work.

---

### Post by eon01 on 2013-11-18
> **oldfred said:**
> Please copy code from terminal and if longer post inside code tags. You can easily add code tags by using advanced editor and highlight code and click on # icon in edit panel at top.

You are only showing one large partition and swap inside an extended partition.

Does deeper search in testdisk show more old partitions. It may find multiple versions or overlapping older partitions and only some choices of recovery that do not overlap will work.

Sorry I cannot copy the code since I don't have a wireless connection in the other laptop, and I am running a command line only distro . 
(A part of) Testdisk output : 
[http://i.imgur.com/uZQcr0e.png](http://i.imgur.com/uZQcr0e.png)

I tried different live usb ditro, hoping that one of them will detect my /home . 
Edit : 
Here is the output of boot-repair : [http://paste.ubuntu.com/6437066/](http://paste.ubuntu.com/6437066/)
Here is the output of parted -l  : [URL="http://i.imgur.com/I9KWR1Y.png"]http://i.imgur.com/I9KWR1Y.png

[/URL]

---

### Post by grahammechanical on 2013-11-18
You do not have a /home partition. That is the problem. Sorry. Linux Mint is on sda1 and sda5 is a logical partition inside the extended (sda2) and it is used as swap partition. There should be an sda3 and sda4. Do you have a partition that is not formatted? That may be why you are missing 3 and 4. I have the same situation on one of my hard disks. I think that it is because I created two partitions but I did not install (hence format) an OS into them. Is your /home partition encrypted? I am just guessing at possibilities.

Regards.

---

