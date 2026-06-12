---
title: "Want to create a Ubuntu OS backup"
date: 2013-02-25
forum: General Help
---

### Post by Ralph L on 2013-02-25
I run Ubuntu 12.04.1.  I have had problems with installing updates.  In fact I am just completing a new clean install, because I installed updates a week ago and it caused system problems.  I have a large number of additional items installed (including user accounts and special profiles for Thunderbird and Firefox) and it has taken me a considerable amount of time te get everything reinstalled.

Now I want to create a backup of my OS so that I can just reinstall what I have running now in case I have more problems with updates.  I hope to be able create a "Live CD" with all my stuff (including profiles, scheduled tasks, and user accounts) on it, from which I can boot and do an install on a new partition on my hard disk.  By searching the web I found "remastersys" recommended for older systems, but the web site cautioned that it sometimes didn't work correctly for Ubuntu 12.04 and newer.

Has anybody been able to use remastersys to backup and restore a 12.04 system?  If so, what was the procedure with which you were successful?  Did you do a restore to ascertain that part really worked?  Did it restore user accounts, special profiles and configurations?  Are there any other programs that are better than remastersys?  Please note that all my data files are on a separate partition that I backup separately using Luckybackup.

I also found Quickstart [http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart) that will bit for bit copy file systems.  Has anybody used this as an OS backup.

Thanks

---

### Post by Bucky Ball on 2013-02-25
You might also look here:

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by JiuJitsu500 on 2013-02-25
+1 for CloneZilla - used it a few times as a backup or when I gave a friend a bigger HDD and wanted to transfer everything. Works great.

remastersys is decent too for backing up your entire rig, though it's more for a fresh-install with all of your apps and settings kind of thing. I haven't even tried to use it in a long time though.

---

### Post by offgridguy on 2013-02-25
Make it +2 for cloneZilla

---

### Post by sammiev on 2013-02-25
+3 for cloneZilla and my backup USB drive. I now can do crazy testing as I know I can always restore to what I was in 30 min.

---

### Post by kevdog on 2013-02-25
Thanks for Clonezilla recommendation.

Is this just for Linux installs, or would it back up Windows installations also well (Similar to Norton Ghost or other such disc ghosting software)?

---

### Post by sammiev on 2013-02-25
> **kevdog said:**
> Thanks for Clonezilla recommendation.

Is this just for Linux installs, or would it back up Windows installations also well (Similar to Norton Ghost or other such disc ghosting software)?

I backup my full HD all at the same time which also includes Windows.

---

### Post by Cyphrex on 2013-02-25
Being a newbie to the world of Linux, Clonezilla was suggested to me back in August of 2012 to use to clone Windows machines for lab distribution for public school systems. 

Clonezilla is now my best friend, if only I had more time to experiment with all the extra bells and whistles. This software can be loaded to a CD (when Optiplex 240s with flashed BIOS wont read pen/flash drives; or more recent models that can read the bootable flash drive) and allow you to make a complete duplicate of your system at a time when it was still working.

+4 for Clonezilla. ( Use local device and make sure to select the HDD you want to put the image on for the source (first choice) vs the working HDD you are cloning; recently used a Windows disc to format extra HDD's not used to be removed from computer and formatted my HDD with images on it. Luckily the images were still fresh and only took a little extra time to go grab from each of the labs.)

---

### Post by Ralph L on 2013-02-26
Thanks for all the replies.  I really appreciate it.  I looked at the clonezilla web site, but I still have a few questions.

1.  Does clonezilla really backup and restore a partition bit for bit?  Will my user accounts be restored just as they were on the original source?  Will all my soft links from the restored image still correctly point to files on other partitions.  For example, my "Documents" folder in /home/ralph in my OS partition is just a soft link to a Documents folder on another partition (my data partition).  My Firefox "profiles.ini" file also points to a folder on my data partition that contains the actual Firefox profile.  Will all this be restored exactly as it was when the clone was done?

2.  It appears to me that clonezilla will clone a partition only to another partition, not to a folder/file on another hard drive.  Is this true?  I don't have enough space on my hard drive to store a clone of my OS partition on my main hard drive, so I would like to put it on my USB backup drive.  However, I have all my backups of my data partition on that drive and DON'T want to destroy them.  To use my USB backup drive as a clone destination, would I have to create a new partition on that drive and get that mounted, or could I simply create a new folder on my backup drive and use that a clone destination?

3.  If I somehow manage to get a clone of my OS partition on my backup drive, could I boot from the USB backup drive and then recreate my OS partition in another partition on my hard drive?  I would like to do this for testing the restore capability to see that it really works, without overwriting my current OS partition.

Thanks in advance for any input.

---

### Post by Jocklad on 2013-02-26
This could be very useful.

But cant find  Clonezilla in Software centre.

Jocklad

---

### Post by Jonny87 on 2013-02-26
+ 5 for Clonezilla;
Clonezilla will do what its name suggests. It will make a complete clone of your Hard Dive/Partition. regardless of you have stored on it (Windows or Ubuntu). When you restore it, it will restore EXACTLY as it was. 

Also how are you with CLI or Scripting? May I suggest the following thread, it's old, but should still be completely relevant (just realised it has links to up to date info anyway);
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
This has been my most used method of backup and restore, so I know it works.

---

### Post by Ralph L on 2013-03-04
I was able to create a clone of my Ubuntu 12.04 system (sda11).  And I was able to do a restore to an old partition that I had messed up (sda12).  However, I cannot boot from sda12.  When I select it and press enter, it immediately gives an error message (something like "cannot find device") and quickly returns to the boot screen from which I can select the boot partition.  I can still boot fine to sda11.  One thing I noticed was that the entries on the boot screen for sda12 did not change after the restore.  They still show a couple of recovery options, and still show the old linux version rather the the newer one that is in the cloned sda11.  So I am guessing that I need to enter something into the boot options, but I have no idea what.

Edit:  The clonezilla restore partition seems to have created sda12 with the same UUID that was in sda11, when the image was created.  So now I have two partitions with the same UUID (bad).  In restoring an image to a different partition I followed the directions in [http://drbl.org/faq/fine-print.php?path=./2_System/102_restore_image_to_different_partition.faq#102_restore_image_to_different_partition.faq](http://drbl.org/faq/fine-print.php?path=./2_System/102_restore_image_to_different_partition.faq#102_restore_image_to_different_partition.faq) .  These directions did not mention the fact that the restored partition (sda12) would have the same UUID as the source partition (sda11).  Hence, there were not instructions for dealing with it.

I would appreciate any help.

---

### Post by mike555 on 2013-03-04
check this out ...   [http://www.sudo-juice.com/how-to-change-the-uuid-of-a-linux-partition/](http://www.sudo-juice.com/how-to-change-the-uuid-of-a-linux-partition/)

---

### Post by Ralph L on 2013-03-04
mike555
Thank you very much for responding.  I followed the instruction to create a new uuid and to install it on sda12.  I checked with gparted just to make sure it was installed and it was.  I then did:
```
sudo update-grub
```
I then brought up /boot/grub/grub.cfg in gedit to make sure that it found sda12 with the new uuid and it had.  However, when I restarted, the grub boot menu still contained the old sda12 entries with the same uuid that sda12 had prior to my doing the clonezilla restore.  It seems that update-grub did not rewrite the grub boot menu, even though entries with the new (and correct) uuid were in grub.cfg.  In addition, the old sda12 recovery entries were still in the grub boot menu.  And of course, I could not boot from my newly restore sda12 partition.

Any help is appreciated.

---

### Post by Ralph L on 2013-03-05
See [http://ubuntuforums.org/showthread.php?t=2124458](http://ubuntuforums.org/showthread.php?t=2124458) for how to solve this.

---

