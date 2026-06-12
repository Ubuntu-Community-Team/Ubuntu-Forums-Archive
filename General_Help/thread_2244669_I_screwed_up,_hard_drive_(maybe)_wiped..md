---
title: "I screwed up, hard drive (maybe) wiped."
date: 2014-09-18
forum: General Help
---

### Post by john292 on 2014-09-18
Earlier I was trying to Install Ubuntu to a partitioned section of my hard drive, but the partitions weren't showing up on the Ubuntu installer. A guide I found told me to zap the GPT data and keep the MBR. I did as was instructed (or so I thought) and nothing changed. I decided to take a break from trying to install and go back to Windows 8.1, but there was no boot drive. I reset the BIOS settings back to default but still nothing. Now, in the test version of ubuntu, my hard drive data isnt showing up at all. I made a reddit post ([http://www.reddit.com/r/linuxquestions/comments/2gpu18/while_trying_to_install_ubuntu_wiped_hard_drive/](http://www.reddit.com/r/linuxquestions/comments/2gpu18/while_trying_to_install_ubuntu_wiped_hard_drive/)) and get a reply that seemed like it would help, but I just don't have enough knowedge about ubuntu to fix the problem on my own. Any help would be much appreciated.

My internal backup drive also got wiped so there is no backup. I cannot access anything.

UPDATE: Things are looking better, I ran Testdisk and it found the partitions. I'm a little lost at what to do right now, my partitions are there, so how do I fix the problem?

-John

---

### Post by rbmorse on 2014-09-18
I'm not sure I understand what you meant by "zap the GPT data and keep the MBR".   My read is that you converted a drive from GPT partitioning to MBR partitioning. If so (and I hope it is not) then when you removed the GPT partition(s) from the disk they took whatever data was on them with them. 

The drive may be recoverable...I don't know...but until somebody with more knowledge chimes in it would be a good idea to not create any new partitions on that particular hard drive. 

Your internal backup...was that another partition on the same physical drive, or was that on another physical drive that got wiped, too?

---

### Post by john292 on 2014-09-18
Yeah, I didn't really know what I was doing. The recovery was a  partition on the same disk. Windows 8 came pre-installed on the computer  so I'm not sure how to get that back either. *sigh*

---

### Post by rbmorse on 2014-09-18
Then it's gone.  The drive may be recoverable, as I said above I don't know, but it will take special tools and skills.

---

### Post by redrumrogue on 2014-09-18
I found this for you ... [http://www.linux.com/learn/tutorials/781778-how-to-fix-a-mangled-partition-table-on-linux](http://www.linux.com/learn/tutorials/781778-how-to-fix-a-mangled-partition-table-on-linux)
I've never used this TestDisk application before but it may be worth a shot if you've got no other options!

---

### Post by oldfred on 2014-09-18
If you had Windows 8 pre-installed it uses UEFI to boot and UEFI has to have gpt partitions.
Do you have any documentation on what partitions you had. Like a Boot-Repair info report or parted -l list? That would greatly aid recovery.
Test disk should work, but may not find an essential partition or two. Windows has to have an unformatted partition just before its first NTFS partition and since unformatted may not be found.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Did you just delete all partitions or convert to MBR? If you converted you should be able to convert back.

 [http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
[http://askubuntu.com/questions/460233/cant-restore-my-gpt-data-with-gdisk](http://askubuntu.com/questions/460233/cant-restore-my-gpt-data-with-gdisk)

      
 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by oldfred on 2014-09-18
How did you zap partitions? 
If you used gdisk and its z command that is an erase all partitions. 
From gdisk's instructions:
>  z       zap (destroy) GPT data structures and exit


Or did you convert to MBR?

Have not used testdisk to restore partitions. Its instruction page is pretty good.
Testdisk should give you a list of partitions. If you had changed partitions around it will usually show multiple versions and you have to select the correct set that matches your last version. Differences should overlap start & end so you must make sure your final selection of partitions does not overlap. It should tell you that it is not possible. With gpt all partitions are primary (in effect) so you should not have any issues of primary, extended or logical. Just D for deleted and then resetting the correct partitions back again.

---

### Post by john292 on 2014-09-18
My partitions have been restored, and the boot partition is detected in the BIOS config menu, but it gives me a 0xc0000225 error.

---

### Post by oldfred on 2014-09-18
From Ubuntu live installer run the Boot info report. Post the link it gives you.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

      
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

 Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

If you restore Windows including the system reserved in the main partition then it will not work. 
Also even if off by one sector on restore you have to run chkdsk from your Windows repair CD or flash drive. You cannot run chkdsk from Linux.

---

### Post by john292 on 2014-09-18
Thanks for all the help -- it seems like im almost there! Bootrepair didn't change anything, but the pastebin file ([http://paste.ubuntu.com/8376856/]("http://paste.ubuntu.com/8376856/)might")) might help diagnose the problem.

---

### Post by oldfred on 2014-09-19
I am almost positive that your sda3 is not correct. See post #9, you are missing the system reserved.
And many systems have vendor recovery partition(s) at end of drive which you do not show.
What brand, model system. Maybe someone with same system posted details?

It also looks like you recovered a MBR(msdos) partition table, not a UEFI/gpt partition table. Windows 8 that is pre-installed boots with UEFI and only boots with gpt partitioning.

And if start of the NTFS partition is not correct it will not work. If size is just wrong then chkdsk from a Windows repairCD or flash drive probably would fix it.

Post screen shot from testdisk showing deleted partitions.

---

### Post by Gordonbp531 on 2014-09-19
> **john292 said:**
> Earlier I was trying to Install Ubuntu to a partitioned section of my hard drive, but the partitions weren't showing up on the Ubuntu installer. A guide I found told me to zap the GPT data and keep the MBR.

-John

Can you post a link to this so-called "guide" so we can head over there and tell whoever has published it that it's a lot of dangerous nonsense?

---

