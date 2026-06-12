---
title: "Trying to recover hd files using a live cd: my files are missing?"
date: 2013-04-21
forum: General Help
---

### Post by teeth on 2013-04-21
So I'm receiving the error "no operating system found" when I try to boot from my hd into windows 7. Like the last time this happened, I created a live disc and put it in hoping to recover my files and then just scrap my drive. However, I'm having trouble. I booted in fine, and opened the drive for my OS. But when I try to browse to the location where my files are, the first folder I encounter is empty! 

This is what I'm encountering:
[img]http://img.photobucket.com/albums/v348/Sacara/Screenshotfrom2013-04-21153949_zpsf7a08728.png[/img]

If you look at the bottom right, you see that users has apparently no files in it. When I open it up, nothing ever loads (it remains white). Same goes with documents and settings. It seems I can get to everything else fine, I even backed up stuff from my trash hoping one of it would be an older version of the file I'm hoping to retrieve. I feel like I'm missing something obvious, but after hours of google, I can't find anyone with quite this sort of problem. I don't get any errors, it just doesn't seem to detect any files. 

Please forgive me here, I'm not the most familiar with this sort of thing. I appreciate any help anyone can give me since I'm trying to recover my thesis files 2 weeks before graduation ):

---

### Post by Mark Phelps on 2013-04-22
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

