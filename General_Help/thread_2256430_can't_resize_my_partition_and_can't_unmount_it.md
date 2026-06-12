---
title: "can't resize my partition and can't unmount it"
date: 2014-12-12
forum: General Help
---

### Post by jb181991 on 2014-12-12
[ATTACH=CONFIG]258516[/ATTACH]

I just want to have a dual boot in my Acer E1-410, install Windows 8.1 in my ubuntu 14.04, I followed the steps here in this link [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot). But when I'm about to resize it, I found out that I couldn't do because as you look at the picture above it has a key. I looked for information on how to create partition here in this link [https://help.ubuntu.com/community/HowtoPartition/ResizingPartition](https://help.ubuntu.com/community/HowtoPartition/ResizingPartition) but unfortunately, the answers there wasn't able to solved my problem. I also input the code ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo fdisk -l[/FONT][/COLOR]
```
and this is the result ```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.



Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.



```

So..
What is the Error?
What should I do?
How can I create partition and Install Windows 8.1?

Help me Please..

---

### Post by grahammechanical on 2014-12-12
Are you trying to resize this partition using a Ubuntu live session? It is best to do this from the live session. 

Regards

---

### Post by schragge on 2014-12-12
@jb181991:
You mean this image, don't you? [attach]258515[/attach]

And you're trying to resize */dev/sda5*, right?

[SIZE=-2]BTW, the error from *fdisk* has nothing to do with resizing. You have GPT partitioning scheme ([GUID Partition Table]("http://en.wikipedia.org/wiki/GUID Partition Table")), and *fdisk* works only with older MBR scheme ([Master Boot Record]("http://en.wikipedia.org/wiki/Master boot record")). There's another command-line tool for GPT — [gdisk]("http://manpages.ubuntu.com/manpages/utopic/en/man8/gdisk.8.html"). But you shouldn't use it if you are not an expert. Instead, launch [GParted]("http://manpages.ubuntu.com/manpages/utopic/en/man8/gparted.8.html") from inside the live session like **grahammechanical** said and *fdisk* warning message suggested.[/SIZE]

---

### Post by jb181991 on 2014-12-12
> **grahammechanical said:**
> Are you trying to resize this partition using a Ubuntu live session? It is best to do this from the live session. 

Regards


I'm sorry for the late reply. Actually, it's not Live session anymore, it's Fully installed in my laptop for months now. I just want to install another OS, the option here was to reformat my /dev/sda2 but unfurtunately I don't want to reformat it because I have many important files here.

---

### Post by jb181991 on 2014-12-12
> **schragge said:**
> @jb181991:
You mean this image, don't you? [attach]258515[/attach]

And you're trying to resize */dev/sda5*, right?

[SIZE=-2]BTW, the error from *fdisk* has nothing to do with resizing. You have GPT partitioning scheme ([GUID Partition Table]("http://en.wikipedia.org/wiki/GUID Partition Table")), and *fdisk* works only with older MBR scheme ([Master Boot Record]("http://en.wikipedia.org/wiki/Master boot record")). There's another command-line tool for GPT — [gdisk]("http://manpages.ubuntu.com/manpages/utopic/en/man8/gdisk.8.html"). But you shouldn't use it if you are not an expert. Instead, launch [GParted]("http://manpages.ubuntu.com/manpages/utopic/en/man8/gparted.8.html") from inside the live session like **grahammechanical** said and *fdisk* warning message suggested.[/SIZE]


I'm sorry sir but that is not the image I attached. Here it is [ATTACH=CONFIG]258520[/ATTACH]and Thank you for the reply.

---

### Post by schragge on 2014-12-12
Then you should launch a live session from CD/DVD/USB, and start GParted from there. You cannot resize mounted partition and you cannot unmount partition you're currently working from.

---

### Post by nerdtron on 2014-12-12
If you are still able to boot into windows 8, it's better to resize windows partitions there.

---

### Post by schragge on 2014-12-13
True, but the OP will resize a *Linux* partition. /dev/sda2 is ext4.

---

