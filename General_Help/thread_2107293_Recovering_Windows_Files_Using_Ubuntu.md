---
title: "Recovering Windows Files Using Ubuntu"
date: 2013-01-21
forum: General Help
---

### Post by exposrule on 2013-01-21
I have both Windows 7 and Ubuntu installed on my computer.  Last night my Windows froze and upon attempting to restart I was given a blue screen of death with the Unmounable Boot Volume error.  All methods of attempting to remedy this have failed.  At this point I would just like to retrieve my files using Ubuntu (which still works fine) and do a clean restore of Windows.  However, I can't seem to figure out how to access my Windows files on Ubuntu, which I only installed a month ago so am not very proficient with as of yet.  I have gone to the Computer folder in Ubuntu and selected the "750 GB Hard Disk", but get the following error: "Unable to mount location.  Can't mount file".  

Any ideas?

---

### Post by alphaamanitin on 2013-01-21
Sounds like damage to the file structure.  What is your setup?  Two HDDs or dual boot from one HDD?  It makes a difference.  If it is two HDD I would use TestDisk to see if you can restore your Windows drive from the backup partition table NTFS has.  I once recovered a Windows XP HDD that I accidentally formatted to FAT32 using TestDisk.  

The other thing you might want to try is the Windows utilities to check the master boot record and rebuild it, it comes on Windows install disks, you can find legit, legal copies online.  Also, you can try SuperGrub.  Hopefully it is just file structure damage and not hardware failure.

AlphaA

---

### Post by Davsdu on 2013-01-21
There's an icon for your Windows partition in the left Unity panel I believe (on mine there is) and it's possible to copy files over to the Ubuntu partition. Otherwise, you can always try to run a Linux live disk and access your Windows partition through that in order to move files to Ubuntu.

---

### Post by Mark Phelps on 2013-01-21
What folks have suggested usually works -- unless -- the Window filesystem has been corrupted, in which case, no matter how you try (folder in Dash, Live CD/USB), that partition is NOT going to be automatically mounted.  Why? Because Linux does that to prevent even more corruption to the filesystem.

Yes, as some folks will tell you, you may be able to FORCE the mounting of the windows filesystem, but that risks ever further corruption -- which is likely to then destroy any chances you have of file recovery.

In my experiences, Windows utilities are best at recovering files from Windows filesystems; Linux utilities, at recovery files from Linux filesystems.

I you are willing to spend money to recovery your Windows files, and have access to a Windows PC (to which you can connect your corrupted hard drive), then read on ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

### Post by exposrule on 2013-01-21
Thanks for the replies.  I am at work and am not able to undergo anything time consuming until this evening, but I think I might try your suggestion [Mark Phelps]("http://ubuntuforums.org/member.php?u=311399").  I don't mind having to spend some money to recover my files.  It will teach me to be more diligent with backing them up in the future.

---

