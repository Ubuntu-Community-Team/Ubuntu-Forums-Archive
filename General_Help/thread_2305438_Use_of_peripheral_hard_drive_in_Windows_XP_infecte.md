---
title: "Use of peripheral hard drive in Windows XP infected PC"
date: 2015-12-06
forum: General Help
---

### Post by AbleTassie on 2015-12-06
I have a friend of modest means who is upgrading from an old Windows XP PC to a newer (but still old) Windows 7 PC. The friend want to transfer files (about 70 GB) from the old XP PC to the newer Windows 7 PC. I think the old XP machine may have some viruses, because the friend's anti-virus program scans regularly and indicates that there are threats that it cannot remove. 

I would like to help and have a peripheral hard drive (160 GB, that is partially full) that I use with the Lubuntu Operating System on another machine. I could use my peripheral hard drive to transfer the files. The hard drive has also been mounted and usable by a Windows XP machine in the past. But I am concerned about getting viruses on my peripheral hard drive and transferring the viruses to my Lubuntu machine.

QUESTION(S): Is the virus concern a legitimate concern? Is there any way to avoid or minimize the chances of picking up viruses and still helping my friend?

Thank you,

Able

---

### Post by Geoffrey_Arndt on 2015-12-06
No, Windows virus's will only run on Windows - - - they hate Linux and they love Windows (for many reasons).    So, no concern.

But one thing you can do is to make a new separate data partition (FAT32 or NTFS) on the spare drive, and only transfer the files there.    When the transfer is done,  you can delete that partition or reformat it for another Linux distro install or whatever purpose you like.

---

### Post by buzzingrobot on 2015-12-06
If the XP's files are infected, they'll be infected on your hard drive, and then still infected, of course, when they're copied back to the new Win7 installation. 

So, it might be useful for your friend to acquire a new antivirus program (I'll guess the one on the XP machine is old).  Then, before copying those files back to the Windows machine, attach the hard drive and run a full virus scan of the drive.)

Antivirus programs need to be updated regularly to ensure they can identify new viruses.

---

### Post by Bucky Ball on 2015-12-06
*Thread moved to **General Help**.*

As far as the Ubuntu portion of this thread is concerned, the query has been answered. It is a legitimate concern Windows to Windows and Windows viruses will be transferred to wherever you copy them to, but if that is a Linux OS, Windows viruses will have no impact. :)

---

### Post by coldraven on 2015-12-06
After copying the files to your external drive scan them with Clam AV. That way you won't infect the Win7 machine
[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

---

### Post by Habitual on 2015-12-06
> **coldraven said:**
> After copying the files to your external drive scan them with Clam AV. That way you won't infect the Win7 machine
[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)It should be noted the clamAV does not clean infected files, but it can and does identify most, but notably it can delete the infected files.
Do NOT enable PUA or you'll see twice as many 'hits' from 'suspect' files and not just actual infected ones.

---

### Post by AbleTassie on 2015-12-06
> **Geoffrey_Arndt said:**
> No, Windows virus's will only run on Windows - - - they hate Linux and they love Windows (for many reasons).    So, no concern.

But one thing you can do is to make a new separate data partition (FAT32 or NTFS) on the spare drive, and only transfer the files there.    When the transfer is done,  you can delete that partition or reformat it for another Linux distro install or whatever purpose you like.

Thanks to everybody for their replies. One question. Does making a separate partition really help a lot? Does it help in terms of Windows virus infection? (I do run Windows XP in virtualbox with Lubuntu as the host OS, but my guess is that does not mean much in terms of potential Windows virus infection.) Perhaps making a separate partition will help assure that the Windows machine can mount the external drive?

How do I make a separate partition on the external hard drive? Do I use GParted? Is GParted hard to use? I have read that you run the risk of losing the data on your drive if something goes wrong while using GParted.

Thanks,

A.

---

### Post by sudodus on 2015-12-06
Yes, it helps to make a separate partition or to have a separate drive for this purpose. You make a suitable file system for Windows in that partition. You keep these files in a separate place, and can easily remove them afterwards. As described before, we think that linux is immune.

Gparted is a good tool with a graphical interface, that is intuitive and easy to use.

***Editing partitions is always risky***. So you should have a good backup (somewhere else) before doing it. The safest way is to use a separate drive for this purpose. At least, you should ***not*** use the drive, where you have your backup.

---

### Post by AbleTassie on 2015-12-06
Thanks, it appears that NTFS is the preferable file system for Windows XP and Windows 7.

A.

---

### Post by AbleTassie on 2015-12-06
> **sudodus said:**
> 
Gparted is a good tool with a graphical interface, that is intuitive and easy to use.

***Editing partitions is always risky***. So you should have a good backup (somewhere else) before doing it. The safest way is to use a separate drive for this purpose. At least, you should ***not*** use the drive, where you have your backup.

Thanks Sudodus,

Does "editing partitions" include simply deleting the partition? That is, is deleting a partition risky too?

Thanks,

A.

---

### Post by yancek on 2015-12-06
Bookmark the link below to the GParted Manual which is about as detailed as anything you will find.  Complete with Table of Contents if you are looking for something specific.  Deleting a partition also deletes all data on it.  Modifying partitions with any partition manager is always risky so backups should always be made first.

[http://gparted.org/display-doc.php%3Fname%3Dhelp-manual](http://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

ntfs has been the filesystem used by windows with Desktop versions from at least windows 2000.

---

### Post by AbleTassie on 2015-12-06
Thanks Yancek.

---

### Post by sudodus on 2015-12-07
> **AbleTassie said:**
> Thanks Sudodus,

Does "editing partitions" include simply deleting the partition? That is, is deleting a partition risky too?

Thanks,

A.

Yes, because you might delete the wrong partition.

---

### Post by AbleTassie on 2015-12-15
Thank you to everybody, especially Sudodus and Yancek. I am going to mark this thread as SOLVED.

A.

---

