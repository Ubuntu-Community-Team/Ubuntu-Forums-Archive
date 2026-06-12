---
title: "[SOLVED] XP boot loops in GRUB"
date: 2008-03-02
forum: General Help
---

### Post by momist on 2008-03-02
Hi everyone, I hope someone can help.  After several weeks of using Ubuntu happily, I want to go back into WindowsXP for a single task.  Unfortunately, after having a crash involving XMMS, it seems there's something wrong with GRUB.  Booting into Ubuntu works fine, but when I select the WinXP option it simply reboots and launches GRUB again in a continuing loop.  Here is part of my current partition table, from fdisk:

```

ian@attercop:~$ sudo fdisk -l
[sudo] password for ian:
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x4274 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8b0f8b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3076    24707938+   7  HPFS/NTFS
/dev/sda3            3077        3738     5317515    5  Extended
/dev/sda5   ?       73212      189591   934819511+  65  Novell Netware 386

```

Ubuntu can see and read/write the Windows partition OK, so there's nothing wrong with it that I can see.

I also have sdb with 3 FAT partitions and SDC with the Linux installation.  The MBR I think is on sda (hd0,0).  I've considered putting in the Windows disk and restoring the MBR, but hesitate to go through the pain of recovering GRUB again.  Is there another way?  If GRUB is working OK where else will the problem lie?  

Additional information that may or may not be relevant:  Although  Ubuntu boots normally, it will no longer shut down, but hangs at the Ubuntu exit screen with the progress bar run down right to the end.  The only way out of that is a hard power down with the on/off switch held in for 10 seconds. 

I was having fun, but this has taken the gloss off.:confused:

Ian

Well, thanks to herman, I discovered the use of ms-sys and gave my machine an XP MBR.  The windows system will STILL not boot, it simply loops continuously.  Thanks to SuperGrubDisk, I can get back into Ubuntu, so here I am.  I guess that this is therefore a windows problem, and shouldn't expect help from here.

---

### Post by Nzer24 on 2008-03-02
I haven't heard of this problem before. If GRUB encountered a boot problem, it should print an error message. I would use the SuperGRUB disc again and double check the boot commands for windows.

It could be that a hard drive fault wiped out important windows files. Just because you can view it in linux doesn't mean it works. That sounds a bit more likely, but if that really is the case, you would have to reinstall windows.

If you haven't been able to use windows since you installed Ubuntu, some files might have been corrupted during resizing of the windows partition. I don't think they are wise to allow people to resize partitions without warnings.

---

### Post by lha on 2008-03-03
Given that fdisk prints those warnings, there must be something wrong with your partition table. [Gpart]("http://www.stud.uni-hannover.de/user/76201/gpart/") might be able to help you. Do I need to say that backing up important files is a good idea in your situation?

---

### Post by momist on 2008-03-03
Thanks lha and Nzer24,

I've come to the same conclusion, that I need to reinstall Windows.  Since I'll be doing this, and I have several hard drives, I'm going to rearrange everything, which means also reinstalling Ubuntu.  Wish me luck!

BTW, I didn't re-size the windows partition, so that's not the cause.  However I've had several freezes in Ubuntu which could only be exited by a power down or reset, and if the windows partition was mounted, perhaps this has been the cause?  I'll be more careful of that in future, and unmount whenever I've finished with it. 

Now then, how do I flag this thread 'solved'?

Ian

---

### Post by momist on 2008-03-04
I have deleted WindowsXP entirely, and now only have Ubuntu.  This solved my boot looping problem!  Now I only have to figure out how to do _everything_ in Linux.  :lolflag:

Ian

---

