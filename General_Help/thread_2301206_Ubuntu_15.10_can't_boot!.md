---
title: "Ubuntu 15.10 can't boot!"
date: 2015-10-31
forum: General Help
---

### Post by TBK on 2015-10-31
I installed Ubuntu 15.10 few day ago but I don't know why, now my Ubuntu can't boot to use.
After choosing Ubuntu 15.10 in Grub, I see this (see the image: [https://drive.google.com/file/d/0B0YPxoTYHWAZbjZadkRtcUNiMU0/view?usp=sharing](https://drive.google.com/file/d/0B0YPxoTYHWAZbjZadkRtcUNiMU0/view?usp=sharing))
Help me! I don't want to reinstall Ubuntu.

---

### Post by sudodus on 2015-10-31
The file system is damaged. You should try to repair it.

Boot from a live drive, for example your Ubuntu install DVD or USB drive. Then identify the partition with your installed system. It seems to be **/dev/sda5**, but you should check how it is identified from the live drive. Make sure that the drive is unmounted. Finally repair with ***e2fsck***.

```
sudo parted -l  # "minus ell" helps identify the drive
sudo lsblk  # helps identify the drive
sudo umount /dev/sdxy
sudo e2fsck -f /dev/sdxy
```

where x is the drive letter and y is the partition number. It is probably /dev/sda5, but might be something else.

---

### Post by Bashing-om on 2015-10-31
TBK; Hello;

Have you tried to follow what the system advised ? Run a file system check/repair ... at this point I would run the check/repair form a liveDVD(USB) . Do you have a live 15.10 disk available ?

[INDENT][INDENT]smart system
[INDENT][INDENT][INDENT]we have here
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by TBK on 2015-10-31
I don't have much experience about repairing Linux OSs, I only have used live Ubuntu/Mint to repair Grub so I don't now what to do.
I have live Ubuntu 15.10 in a USB

---

### Post by Bashing-om on 2015-10-31
TBK; Hey ...

"I don't have much experience" -> Not a problem, we can and will walk you through this.
Boot the liveUSB in "try ubuntu" mode and activate a terminal ( key combo ctl+alt+t) and provide the 1st 2 outputs that sudodus recommended:
```

sudo parted -l  # "minus ell" helps identify the drive
sudo lsblk  # helps identify the drive

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

To identify the target partition that contains the file system. With that we point the utility to do it's thing.

[INDENT][INDENT]ain't nothing to it
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-10-31
The last time I looked recovery mode has an option to check all file systems. At the Grub boot menu select Advance Options for Ubuntu and then select recovery mode and at the recovery menu select fsck. When the file system check is complete you will be back at the recovery menu. Then select Resume - resume normal boot.

Regards.

---

### Post by TBK on 2015-11-01
I tried recovery mode but the recovery menu didn't appear

---

### Post by yancek on 2015-11-01
Are you trying to boot the Recovery on the installed system?  Use the installation medium you used and run the command suggested by opening a terminal when you get to the Desktop, type the following:

```
sudo e2fsck -f /dev/sda5
```

Unless there was some kind of hardware failure or a power failure, something like this would not happen without some modification to the system.  Did it ever work?

---

### Post by TBK on 2015-11-01
Right now I'm in a Ubuntu live 15.10 USB

I have used 
```
sudo e2fsck -f /dev/sda5

ubuntu@ubuntu:~$ sudo e2fsck -f /dev/sda5
e2fsck 1.42.12 (29-Aug-2014)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
UBUNTU: 304856/3055616 files (0.5% non-contiguous), 7958910/12215576 blocks
```

---

### Post by Bashing-om on 2015-11-01
TBK; Hello ;

The e2fsck output looks good; no errors reported.

What now results when you boot the install ?

[INDENT][INDENT]maybe all good
[/INDENT][/INDENT]

---

### Post by TBK on 2015-11-01
Now I can boot into Ubuntu.
Thank everyone!

---

### Post by Bashing-om on 2015-11-01
TBK; Great !

The system did tell us what to do, we just followed the bread crumbs .
Some kind of smart, huh !

As this situation is concluded ->
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]Up Up and Away
[/INDENT][/INDENT]

---

