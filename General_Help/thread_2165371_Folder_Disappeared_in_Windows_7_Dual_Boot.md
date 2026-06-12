---
title: "Folder Disappeared in Windows 7 Dual Boot"
date: 2013-08-04
forum: General Help
---

### Post by red72 on 2013-08-04
I am running 13.04 dual boot with Windows 7.  Ubuntu is stalled on a second hard drive.  Windows 7 is on the original hard drive and I added a second partition on this hard drive where I keep some files and folders.  All has been working fine for a few months.  Two days ago I made a new folder and copied some movies over from a server using ftp.  I shut down, restarted and watched a movie no problem.  Then the following day I noticed the new folder and files are missing.  The only thing I can think that happened is I (shutdown Ubuntu) started Windows to do one quick thing I can only do in Windows.  It seems the movies are still there because when I add up the files that are still on the partition and then look at the partition properties there is a 10GB difference.  

Two questions:
1) Is there any quick and easy way to get the files back?  I don't want to jeopardize my Windows 7 as I need it for critical work one a month.
2) And this is more important, why did this happen?  Can I still trust my system to keep my files safe?

Thank you for your help.
Patrick

---

### Post by Mark Phelps on 2013-08-04
A frequent cause of this problem is Windows hibernation. If you hibernate Win7, that will save the directory table of the shared data drive.  The next time you awaken Win7, it will rewrite the directory tables of the shared data drive with its saved copy -- thus "removing" the files.

---

### Post by red72 on 2013-08-05
I did not hibernate Ubuntu or Windows so that is not it.  Just to make sure, I logged in to Windows again and logged out again.  Still no folders or files.  Also, I noticed a new test folder I made in Ubuntu is also missing.  So whatever the issue is affects all my new folders.  

Below is the partition I am having problems with.  Why is there a partition 3 ("Extended Pattition") and 5 covering the same area?  I assumed there should be just one partition.  

[ATTACH=CONFIG]245083[/ATTACH]
[ATTACH=CONFIG]245084[/ATTACH]

---

### Post by red72 on 2013-08-14
Bump.  Can anyone help with this?
Thanks,
Patrick

---

### Post by red72 on 2013-08-30
Please, can someone help?  Thanks, Patrick

---

### Post by oldfred on 2013-08-30
An extended partition is just a container for all the logical partitions you have. You just happen to have one logical that is using the entire extended. That is ok.

Have you tried testdisk and its deeper search?
       
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

      
 repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)


 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

Also NTFS version, many report good success but not free.

 Testdisk & photorec
you want to try some others there are magicrescue ; foremost and scalpel 
Deleted file alternatives this user liked but not free
[http://ubuntuforums.org/showthread.php?t=1339278](http://ubuntuforums.org/showthread.php?t=1339278)
"GetDataBack for FAT" was the most successful one among the ones that I've tried. Though it couldn't recover folder's names, it recovered all the files' and sub-folders' name. And it's much better than the others did. Thanks!

---

### Post by red72 on 2013-09-04
Thank you for the feedback.  Since I am a beginner all these options quickly overwhelmed me.  So I decided to reformat the partition and hope that the issue does not happen again.
Best,
Patrick

---

