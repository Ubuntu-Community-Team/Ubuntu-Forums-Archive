---
title: "Chmod and Chown don't work?"
date: 2006-07-11
forum: General Help
---

### Post by kewldude606 on 2006-07-11
I have some files that are owned by root that I want to change to be owned by me (my username is daniel).  First I did ```
sudo chown -R daniel:daniel *
``` This changed most of the files, but some remain.  Neither chmod or chown affect these files!  Chmod doesn't return anything, but the permissions don't change.  **Sudo chown daniel:daniel *** returns an error: ```
chown: changing ownership of `KATG-2006-06-27.mp3': Operation not permitted
``` (there are one of these for all of the files).

Here is another tidbit I find interesting...
```
cd ~/Podcasts/
find | grep DGW
#this returns nothing
```
```
cd ~/Podcasts/Daily\ GizWiz
find | grep DGW
# this returns all of the files with DGW
```
So basically, find doesn't list these files that won't change ownership unless they are in the same directory.

This example works as expected:
```
cd ~/Podcasts/
find | grep TWiT
#this returns a list of files that are in the twit subdirectory.
```
```
cd ~/Podcasts//this WEEK in TECH - MP3 Edition
find | grep TWiT
# this returns the same list as the first part
```

Please help me out here!  Also, sudo su and change the ownership/permissions doesn't work either.

---

### Post by briguy on 2006-07-11
The only thing I can think of is that the files or directory is somehow immutable.  Do a lsattr -R on your directory, and if there is an "i" in the output, the file is immutable.  Unlikely, but possible.  If they are, change it back with the chattr command.

---

### Post by hanzomon4 on 2006-07-11
I had a similar problem, you might whant to fsck your hard drive to see if you have errors. 
Use this [link]("http://ubuntuforums.org/showthread.php?p=1215304#post1215304") for instructions.

---

### Post by kewldude606 on 2006-07-11
> **briguy said:**
> The only thing I can think of is that the files or directory is somehow immutable.  Do a lsattr -R on your directory, and if there is an "i" in the output, the file is immutable.  Unlikely, but possible.  If they are, change it back with the chattr command.
I don't think the right thing happened...```
lsattr: Inappropriate ioctl for device While reading flags on <file>
```
> **hanzomon4 said:**
> I had a similar problem, you might whant to fsck your hard drive to see if you have errors. 
Use this [link]("http://ubuntuforums.org/showthread.php?p=1215304#post1215304") for instructions.
Coincidentally, my hard drive automatically checked itself today because it had been mounted 30 times.  I had this problem before the drive got checked, however.

---

### Post by digby on 2006-07-11
Are the files on a fat32 or NTFS partion by chance?

---

### Post by kewldude606 on 2006-07-12
> **digby said:**
> Are the files on a fat32 or NTFS partion by chance?

Why, yes, it's FAT.

---

### Post by T700 on 2006-07-12
> **kewldude606 said:**
> Why, yes, it's FAT.

Windows partitions don't support Linux permissions.

Paul

---

### Post by kewldude606 on 2006-07-12
> **T700 said:**
> Windows partitions don't support Linux permissions.

Paul

Is there a non-destructive way to change it?  Or a workaround that lets any program write to the drive?  Right now I have to run castpodder as root.

---

### Post by Indras on 2006-07-12
> **kewldude606 said:**
> Is there a non-destructive way to change it?  Or a workaround that lets any program write to the drive?  Right now I have to run castpodder as root.

This is, ironically enough, the same as a problem I was having with Samba.  Here's the HOWTO I wrote on how to fix it:

[http://www.ubuntuforums.org/showthread.php?t=199644](http://www.ubuntuforums.org/showthread.php?t=199644)

Basically, by default, Ubuntu mounts all FAT32 partitions as root:root with permissions 770 (rwxrwx---).  If you want to be able to have some software work okay with it, you're going to need to set up your /etc/fstab to mount it as root:root with permissions 777.

Basically, open your /etc/fstab as root (back it up first, naturally) and under the partition you're having trouble with change "umask=007" to "umask=0".

Then either restart the system, or unmount and re-mount the partition.

---

### Post by briguy on 2006-07-12
FAT doesn't support file ownership.  That's why the lsattr wouldn't work either.

---

### Post by kewldude606 on 2006-07-12
> **Indras said:**
> This is, ironically enough, the same as a problem I was having with Samba.  Here's the HOWTO I wrote on how to fix it:

[http://www.ubuntuforums.org/showthread.php?t=199644](http://www.ubuntuforums.org/showthread.php?t=199644)

Basically, by default, Ubuntu mounts all FAT32 partitions as root:root with permissions 770 (rwxrwx---).  If you want to be able to have some software work okay with it, you're going to need to set up your /etc/fstab to mount it as root:root with permissions 777.

Basically, open your /etc/fstab as root (back it up first, naturally) and under the partition you're having trouble with change "umask=007" to "umask=0".

Then either restart the system, or unmount and re-mount the partition.

Thanks man, that worked!  Now everything is 777!

Thanks to everyone who posted.  As a weird coincidence, now I'm getting 1.5MB/s down instead of 1MB/s down...

---

