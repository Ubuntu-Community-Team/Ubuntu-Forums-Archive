---
title: "Accidentally overwrote a ntfs partition with the ubuntu installation"
date: 2014-03-14
forum: General Help
---

### Post by arthur4 on 2014-03-14
hey people, please help me!
I accidentally overwrited my ntfs partition with a encrypted linux one, in panic i stopped the installation on the middle of the procces, then re-forated it to ntfs and tried recovering my files with testdisk, no success of course, I know I should have searched about it first, is there anything I can do [COLOR=#545454][FONT=arial]?[/FONT][/COLOR]

---

### Post by arthur4 on 2014-03-15
If I install windows 8.1 there again, is there any tool i can use fro ubuntu live cd to recover files

---

### Post by QIII on 2014-03-15
That would simply make matters worse, as portions of your partitions would actually be over-written, adding to the obscuration.

Unfortunately, formatting can be a pretty destructive process.  If you have already used TestDisk or Photorec without success, I'm somewhat less than confident you will be able to recover much.

However, since these were files on a Windows partition originally, Windows tools may be the best way to recover them ... if that's possible at all since you started your formatting as encrypted and then reformatted over that.

I'm not familiar with those tools and can't remember their names right off the top of my head, but a couple of regular users know of them.  I'll see if anyone is around and see if we can't get you some help here.

NOTE:  Don't do anything more with the partitions right now!  The more you do, the less likely the recovery.

---

### Post by arthur4 on 2014-03-15
Ok, thanks! I'm going to use phoorec to recover the photos i lost 

I failed to use testdisk because I was trying to recover the partition itself, but now that I found a 3 week old backup(which doesn't have my photos), all i really need are those photos.

---

### Post by arthur4 on 2014-03-15
I'm going to die! It's working!!!!!! thanks qlll for pointing out photorec!

---

### Post by Mark Phelps on 2014-03-15
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from [http://getdata.com](http://getdata.com).
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to their website, you can compare versions and features.

Your data ... your money ... your choice.

---

