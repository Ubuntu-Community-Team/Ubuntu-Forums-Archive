---
title: "Danger to XP OS and Installed Software if I install Dual Boot Ubuntu"
date: 2014-11-18
forum: General Help
---

### Post by robert137 on 2014-11-18
I've seen the advice to backup before installing Ubuntu along side my existing Win XP that is already installed.  No problem backing up my data.  But what I'm curious about is what is the risk of something going wrong to where I'd have to reinstall Windows or my software.  That would cause problems I'm not prepared to deal with right now.  Loss of stored data is not a problem and can be backed up.

I do have a D partition on this Eee PC XP machine that I am looking to install Ubuntu onto.  Could I install Ubuntu onto the D drive and thereby safely avoid (if there is risk to my OS and software on C) even touching what is currently installed on C drive?

What's the safest and most effective way to do this, given the concerns I've expressed?

I was going to try running both with Virtual Box or VM, but a) it seems I  may not have the resources to run it all very well (2 G Ram) and my first attempt with VB, it seems there was something it didn't like about my old XP system?  If I can safely do a dual boot, maybe that can suffice?

Suggestions?
Thanks!

---

### Post by Frogs Hair on 2014-11-18
You might want to post a snip of the XP partition table here to get some opinions. I'm not familiar with that computer, but know if you already have four partitions installation is more difficult. I haven't dual booted with XP before either.

---

### Post by Mark Phelps on 2014-11-18
> I do have a D partition on this Eee PC XP machine that I am looking to install Ubuntu onto. Could I install Ubuntu onto the D drive 

Basically -- NO.  A "D" drive is a partition that contains a Windows filesystem.  Linux installation needs a Linux filesystem.

> What's the safest and most effective way to do this, given the concerns I've expressed?

The "safest" way involves first, doing an image backup of your Windows partitions to an external drive.  If you can't do that, you risk losing at least the data, and possibly the OS, if anything goes wrong.

To find out what you have on your drive at present, boot from Ubuntu install media, open a terminal, enter "sudo fdisk -lu" (lowercase L, not a one) -- and post the result of that command back here.

Once we know what's on your disk, we can better provide detailed advice.

---

### Post by robert137 on 2014-11-18
Thanks for the reply.  And how would I copy and paste the "partition table"?  I haven't the first clue?

---

### Post by deadflowr on 2014-11-18
> **robert137 said:**
> Thanks for the reply.  And how would I copy and paste the "partition table"?  I haven't the first clue?

> To find out what you have on your drive at present, boot from Ubuntu  install media, open a terminal, enter "sudo fdisk -lu" (lowercase L, not  a one) -- and post the result of that command back here.

By install media it means that Ubuntu's installation media, either cd/dvd or usb stick, allows you to run a test drive, without installing anything.
When you boot the disk/usb, it'll let you load the (test)live session. It is the first option, and should default to it.
(It's listed as Try Ubuntu)
From with that, when it loads, (it might take sometime) press ctrl + alt + T and a terminal window will open.
copy the above command then highlight and copy the output.

It is unknown how the Internet connection would be for you on the live session, but if it works after you copy the output, open firefox and log into the forums from there, and paste the output into this thread.

Hope that helps.

---

### Post by yancek on 2014-11-18
I think the best thing you can do is read a tutorial or some tutorials on installing Ubuntu so you understand a little about what you are doing before you start.  The link below is to one such site which is quite a lot more detailed than most and also has some useful information on Linux partition terminology and partitioning.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by mastablasta on 2014-11-19
you likely do not have the resources for virtual machine. furthermore you might need a 32bit version of the OS (not sure about that) and you might want to try something lighter such as Xubuntu (depending on the specs, RAM is just one component the next is disk space and then processor and graphics chip)

also do the backup using some free tools such as Redo Backup or Clonezilla. If something goes wrong you can just reimage the disk and restore the whole disk to it's previous state. no need for reinstall on windows or anything like that.

chances for things to go wrong are small but they are there. especially since you will be moving and resizing the current disk partition. when doing that there is always some risk involved. to remove the risk we do the backup (usually system image) to another disk.

before moving/resizing partition make sure you run the check disk at least two times on your current setup.

to copy data from terminal in Linux - mark text in terminal, right click and then select copy.

---

### Post by stalkingwolf on 2014-11-19
I have installed and run 12.04, zorin, mint 13 mate and ultimate edition on eee's both the 1gb and 2 gb versions.  What is currently on the D drive? How big is it?

---

### Post by pqwoerituytrueiwoq on 2014-11-19
> **robert137 said:**
> I've seen the advice to backup before installing Ubuntu along side my existing Win XP that is already installed.  No problem backing up my data.  But what I'm curious about is what is the risk of something going wrong to where I'd have to reinstall Windows or my software.  That would cause problems I'm not prepared to deal with right now.  Loss of stored data is not a problem and can be backed up.the risk is low IMO, but it never hurts to make a backup
some people have accidentally deleted there windows partition, which can lead to a very very bad day

---

### Post by robert137 on 2015-01-25
hi,
sorry it's taken me so long to get back to this project.  I tried to enter the above command, but it's not recognized.  This was a little unclear.  Can you clarify the exact command?

To find out what you have on your drive at present, boot from Ubuntu  install media, open a terminal, enter "sudo fdisk -lu" (lowercase L, not  a one) -- and post the result of that command back here.  

Thanks!

---

### Post by monkeybrain20122 on 2015-01-25
XP? Kill it.

---

### Post by Mark Phelps on 2015-01-25
> Can you clarify the exact command?

I gave you the "exact command": sudo fdisk -lu

---

### Post by QIII on 2015-01-25
Perhaps this would be clearer for you.

```
sudo fdisk -lu
```

Copy it and paste it in the terminal.

---

### Post by robert137 on 2015-02-17
My D drive is 72 GB with 65 free.  Thanks for any advice!

---

### Post by robert137 on 2015-02-18
Finally, I've gotten back to this issue.  Here is the information you requested, based on that command.  I look forward to any advice.  Yes, I have gone ahead and mirrored my system, just in case:  


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x355aa9d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   151123454    75561696    7  HPFS/NTFS/exFAT
/dev/sda2       151123455   302230844    75553695    7  HPFS/NTFS/exFAT
/dev/sda3       302230845   312480314     5124735   1c  Hidden W95 FAT32 (LBA)
/dev/sda4       312480315   312576704       48195   ef  EFI (FAT-12/16/32)

Disk /dev/sdb: 8011 MB, 8011087872 bytes
247 heads, 62 sectors/track, 1021 cylinders, total 15646656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  3224498923  3657370039   216435558+   7  HPFS/NTFS/exFAT
/dev/sdb2   ?  3272020941   930513678   976730017   16  Hidden FAT16
/dev/sdb3   ?           0           0           0   6f  Unknown
/dev/sdb4        50200576   974536369   462167897    0  Empty

Partition table entries are not in disk order
ubuntu@ubuntu:~$

---

### Post by bashiergui on 2015-02-18
If you cannot afford to lose the XP partition and you have no way to reinstall it, then it sounds like the risk is too high in this case. Why must you dual boot? Consider getting another computer and put Linux on it. You can get very old cheap hardware to run modern linux pretty efficiently.

---

