---
title: "Backup Windows 8 from Live Ubuntu usb"
date: 2013-11-14
forum: General Help
---

### Post by childintime on 2013-11-14
Hello, I have installed Windows 8 and Ubuntu, but neither OS boots, I can only access Grub terminal. It is possible to somehow backup my Windows 8 to external HDD using just "Try Ubuntu" option from live USB?

---

### Post by Bucky Ball on 2013-11-14
Yes it is. Simply boot from the LiveCD and backup what you want to where you want. That easy.

As for your other issue, tried using Boot Repair?

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Please post a new thread in ***Installation & Upgrades*** regarding the boot issue rather than confusing it with the issue outlined in the title of this thread. You will get more support for it that way. ;)

---

### Post by childintime on 2013-11-14
Dear Bucky Ball, I am kind of new to linux, so that's what I am asking, how should I do it? I have only one USB, so I cannot burn any backup software into it, like  CloneZilla. 

As for other issue, I tried using Boot-Repair but it does not solve the issue. And I already have a topic about it in Installation subforum for quite some time already :)

---

### Post by Bucky Ball on 2013-11-14
Okay. Well, boot from the LiveCD, open a file manager, find your files. Open another file manager window, find the location you want to copy the files to. Drag and drop.

There might also be a backup utility in the Applications menu on the CD desktop. Not sure as don't use a standard Ubuntu install. Have a look, but if there is it might takes ages to do it. Try with a few.

* Note: yep, I looked at your other thread. No luck with fantab's instructions? You have not reported back with the results at all so makes it a bit hard to help. ;)

---

### Post by childintime on 2013-11-14
But where do I find the Windows 8 files? Let's say here are my Windows partitions: [http://i.imgur.com/SXaqHrR.png](http://i.imgur.com/SXaqHrR.png) but I can neither open them, nor Mount & open, nothing works.

And yeah I am following fantab's advice, but as he said first it's better for backup my stuff and that's what i am trying to do.


P.S. sorry for simple question, it's 3rd day i am using Linux :P

---

### Post by Bucky Ball on 2013-11-14
Got you. Be VERY careful with this.

Open a terminal and type:

gksudo nautilus

Now you should be able to do what you want. 

CAUTION: Only move the files to where you want them, then shut the file manger. The command I gave opens the Nautilus file manager as root and that can be dangerous, so don't play around with anything else. Do what you need to do and move on. ;)

If that command doesn't work, post back with what the result was.

---

### Post by childintime on 2013-11-14
When I typed, came error: "Nautilus could not create the required folder   "/home/shirley/.config/nautilus".  Before running Nautilus, please   create the following folder, or set permissions such that Nautilus can   create it."
Then I typed this: "sudo mkdir /root/.config/nautilus", repeated your command and it worked, that's what I get: [http://i.imgur.com/gyEIb36.png](http://i.imgur.com/gyEIb36.png) I can't see any Windows 8 files.

---

### Post by VMC on 2013-11-14
I think gparted comes with the livecd. Also, what type of backup are you wanting - just copy partition to partition on the external drive, of cloning the partitions.
Gparted can copy the partitions.

what's the output of the terminal command (using Ctrl+Alt+T for terminal) , then type: ```
sudo fdisk -l
```(that's lowercase L)

---

### Post by childintime on 2013-11-14
VMC, well is it possible to do complete backup of Windows image via ubuntu live usb? Anyways, I would be happy with just simple copy to my external drive, but so far i can't access the windows files as you can see.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x2bfb4dc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   410318847   204800000    7  HPFS/NTFS/exFAT
/dev/sda3       410318848  1155399679   372540416    7  HPFS/NTFS/exFAT
/dev/sda4      1155401726  1456668671   150633473    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      1155401728  1213992959    29295616   83  Linux
/dev/sda6      1213995008  1221806079     3905536   82  Linux swap / Solaris
/dev/sda7      1221808128  1222293503      242688   83  Linux
/dev/sda8      1222295552  1456668671   117186560   83  Linux

Disk /dev/sdb: 2092 MB, 2092957184 bytes
129 heads, 32 sectors/track, 990 cylinders, total 4087807 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf842da10

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     4087806     2043887+   6  FAT16
```

---

### Post by VMC on 2013-11-14
Do you want to figure out why it won't boot or copy Windows or both?
Download and run bootinfoscript(see my blue link) then copy&paste back here between code tags.

Also how was your system installed - ubuntu first or windows first?

---

### Post by Bucky Ball on 2013-11-14
> **VMC said:**
> Do you want to figure out why it won't boot or copy Windows or both?
 first?
 OP wants to know this:

> Backup Windows 8 from Live Ubuntu usb 

Please stick to one issue a thread and read posts in the thread. Gets confusing otherwise. OP can not access the Windows files. Thats's what their asking for help with. Already advised to start new thread for boot issue. Thanks.

---

### Post by VMC on 2013-11-15
> **Bucky Ball said:**
> OP wants to know this:



Please stick to one issue a thread and read posts in the thread. Gets confusing otherwise. OP can not access the Windows files. Thats's what their asking for help with. Already advised to start new thread for boot issue. Thanks.
Why not let the OP answer the question.

---

### Post by fantab on 2013-11-15
OP originally has a booting issue: [http://ubuntuforums.org/showthread.php?t=2187335](http://ubuntuforums.org/showthread.php?t=2187335)

---

### Post by Bucky Ball on 2013-11-15
> **fantab said:**
> OP originally has a booting issue: [http://ubuntuforums.org/showthread.php?t=2187335](http://ubuntuforums.org/showthread.php?t=2187335)

@VMC: Reply to the booting issue on that thread rather than here. This one is about backing up and, I repeat, dealing with two support issues on one thread can become confusing (which is why OP has started another thread to deal with the other issue). The title of this thread has nothing to do with booting issues so apart from confusing, future travellers will not find any helpful information given about it here, but they will on the other thread with the appropriate thread title. Thanks.

---

### Post by childintime on 2013-11-15
Well guys, I fixed MBR using Windows DVD and booted Windows 8 and backed up my data. :)

---

### Post by Bucky Ball on 2013-11-15
All good. Please mark thread as solved using the instructions in my signature. Thanks. ;)

---

