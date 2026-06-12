---
title: "trying to recover data off of hdd"
date: 2012-12-12
forum: General Help
---

### Post by yawnmoth on 2012-12-12
When I type in sudo ntfsfix /dev/whatever I get the following:

```
ubuntu@ubuntu:/media$ sudo ntfsfix /dev/sdf1
Refusing to operate on read-write mounted device /dev/sdf1.
ubuntu@ubuntu:/media$ sudo ntfsfix /dev/sdg1
Mounting volume... ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read $AttrDef, unexpected length (-1 != 2560).
FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Going to empty the journal ($LogFile)... OK
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read $AttrDef, unexpected length (-1 != 2560).
Remount failed: Input/output error
ubuntu@ubuntu:/media$ 
```
Amy ideas as to what my options are?

---

### Post by Wim Sturkenboom on 2012-12-12
Not the specialist on the subject but, from the error, I guess you're supposed to run it on a partition that is not mounted. Is it mounted?

---

### Post by Mark Phelps on 2012-12-12
The app ntfsfix can only fix trivial NTFS problems; it is not a replacement for Windows CHKDSK.

What you really need to do first, is connect this drive to a Windows PC and run CHKDSK on it.  That might repair the filesystem problems and allow you to mount it in Ubuntu again.

If that doesn't work, you will need to use a Windows utility to recover the data.

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

