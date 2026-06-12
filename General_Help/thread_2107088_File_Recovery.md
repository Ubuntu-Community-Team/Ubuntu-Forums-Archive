---
title: "File Recovery"
date: 2013-01-21
forum: General Help
---

### Post by acer9876 on 2013-01-21
Could someone please help me recover my lost files. I accidently deleted them ( from the recycle bin too ) I am running dual boot with windows 7 i believe, and i have tried the testdisk and undelete process. neither have seemed to work for me. i lost about 200Gb of audio and videos. I believe that my main problem is that i didnt use the system partition to store all those files. i used a seperate partition, now i can only recover temporary files. any help?

---

### Post by Mark Phelps on 2013-01-21
If these files were stored in a NTFS partition, you could do better using MS Windows apps to attempt the recovery. Read more below ...

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

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

### Post by acer9876 on 2013-01-21
well dang. i really wish there was a free way. i guess itll just be alot of time to spend redownloading all the files. thanks for your help though
and if anybody else has any suggestions. please comment

---

