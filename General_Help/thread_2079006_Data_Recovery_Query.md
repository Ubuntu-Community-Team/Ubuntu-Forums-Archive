---
title: "Data Recovery Query"
date: 2012-11-01
forum: General Help
---

### Post by amritmachoman on 2012-11-01
I installed ubuntu 12.10 LTS on my harddisk and by mistake i did erase everything and install ubuntu..and so it erased everything.Now the problem is.. i had very important files on the extended partition on windows 7 (NTFS) so can anybody help me in recovering the data? :-(

---

### Post by Frozen Forest on 2012-11-01
Found this question [http://askubuntu.com/questions/25311/best-tool-to-recover-removed-files](http://askubuntu.com/questions/25311/best-tool-to-recover-removed-files)

Important to note, your files might be possible to recover it all depends on if any data has been written to the location where your previous data was saved, in that case won't it be possible to recover the data. More information can be found here [http://www.webopedia.com/DidYouKnow/Hardware_Software/2002/Erasing_Deleted_Files.asp](http://www.webopedia.com/DidYouKnow/Hardware_Software/2002/Erasing_Deleted_Files.asp)

---

### Post by Wim Sturkenboom on 2012-11-01
Do not use your HD any further; the more you use it, the more of the data that you can recover will be overwritten (and permanently lost).

I'm not sure how far you will be able to recover, but liveCDs or liveUSBs with recovery tools are the way to go.

---

### Post by amritmachoman on 2012-11-01
Thank u guys for reply!:)

---

### Post by Mark Phelps on 2012-11-01
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

