---
title: "How do I recover photos that I had in previous Windows"
date: 2014-10-08
forum: General Help
---

### Post by mazhar2 on 2014-10-08
I had Windows 7 and had a lot of photos in E: partition. Then I installed Windows 8.1 without formatting E: drive, and finally I installed 64-bit Ubuntu 14.04 and accidentally formatted the whole drive. Is there any way to recover those photos?

I have read and tried solutions proposed in some other posts but I would like a recovery tool with simple GUI (simple terminal commands would do too).

Thanks in advance.

---

### Post by stalkingwolf on 2014-10-08
yes . one program that i have used is pandora. i found that it recovered files 3 layers deep on my drives.  at the time it was free been a few years so i dont know now

---

### Post by Mark Phelps on 2014-10-08
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install recuva
5) Launch recuva and see if it can file and recover the files and folders you want.

If that doesn't work, then do the following:
1) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
2) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
3) Select the option to Recover a Drive
4) You will get a list of drive, scroll down to find the one for your USB stick or memory card
5) Select Automatic Driver recovery, press Start button
6) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
7) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

