---
title: "File recovery help please"
date: 2016-03-02
forum: General Help
---

### Post by neuro99 on 2016-03-02
Hi,
I realise that there is a wealth of information available on google and these forums, but I just wanted some direct advice please - as there appear to be numerous options available here.

I was attempting to run a script from [https://github.com/graphific/DeepDreamVideo](https://github.com/graphific/DeepDreamVideo)
it was called 1_movie2frames.sh
I'm still new to ubuntu and the whole command line thing as well as running scripts, so really was just playing around with it to try and get it to work (I think I edited the script so that the first two lines were deleted in an attempt to get it to do something).

I was running ubuntu 14.04 from an external USB stick at the time, and for some reason, it proceeded to delete everything on my stick and 2tb drive that was connected at the time!

I have ordered another external drive for recovery purposes, and I believe the original drive was formatted in NTFS. 

What would be the best way to go about recovering the files on this drive? (all types of files, but the most important are images and videos - treasured memories not all of which were backed up as I could not really afford another new drive)

Many thanks in advance for any help.

Regards,

---

### Post by TheFu on 2016-03-02
Restoring from a backup is the best way, as you suspect.  Once that other drive arrives, you'll be able to make a backup. 

For data recovery, always work off a mirrored bit-for-bit disk. Do not work on the original.  Don't use the original again, except to make a backup (bit-for-bit). Don't powr it on. Don't connect it to any computer.  Use ddrescue to make the bit-for-bit copy.

On the mirrored disk, use testdisk/photorec [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) to recover files. It is ugly and will take much effort.  Restoring from backups will be easier. Boot off a live CD and install the testdisk suite using the package manager, then have at it.

---

### Post by coldraven on 2016-03-03
> **TheFu said:**
> Restoring from a backup is the best way, as you suspect.  Once that other drive arrives, you'll be able to make a backup. 

For data recovery, always work off a mirrored bit-for-bit disk. Do not work on the original.  Don't use the original again, except to make a backup (bit-for-bit). Don't powr it on. Don't connect it to any computer.  Use ddrescue to make the bit-for-bit copy.

On the mirrored disk, use testdisk/photorec [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) to recover files. It is ugly and will take much effort.  Restoring from backups will be easier. Boot off a live CD and install the testdisk suite using the package manager, then have at it.
+1
This is technically quite challenging, see if you can find a local Linux Users Group (LUG) and get some help.

---

