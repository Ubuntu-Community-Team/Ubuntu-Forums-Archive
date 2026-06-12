---
title: "Big Problems!"
date: 2006-11-18
forum: General Help
---

### Post by paulrosenthal on 2006-11-18
Guys,

Please help me, I was installing Ubuntu 5.04 (I know, outdated) and I THOUGHT I resized a 60 gig partition to 56.6GB (Windows XP) and my other to 4.4GB (Ubuntu). I must have in the process deleted my XP. Because now for some reason my Ubuntu (in file browser) says I have like 50GB left! Whatever will I do? I have very, very important files on there. Thanks in advance.

---

### Post by taurus on 2006-11-18
What is the output of this command from a terminal, Applications -> Accessories -> Terminal?

```
sudo fdisk -l
```

---

### Post by paulrosenthal on 2006-11-18
That doesn't work, it flashes away to quickly for me to look, lol.

---

### Post by paulrosenthal on 2006-11-18
Nevermind the last post, lol, I found this:


Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6996    56195338+  83  Linux
/dev/hda2            6997        7296     2409750    5  Extended
/dev/hda5            6997        7296     2409718+  82  Linux swap / Solaris
paul@ubuntu:~$

So, am I screwed?

---

### Post by taurus on 2006-11-18
> **paulrosenthal said:**
> Nevermind the last post, lol, I found this:


Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6996    56195338+  83  Linux
/dev/hda2            6997        7296     2409750    5  Extended
/dev/hda5            6997        7296     2409718+  82  Linux swap / Solaris
paul@ubuntu:~$

So, am I screwed?
Sorry mate but you just reformatted your drive to / and swap for Ubuntu!!!

---

### Post by paulrosenthal on 2006-11-18
Anyway to get it back? I really need those files.

---

### Post by taurus on 2006-11-18
Once you've formatted the drive and installed stuff to it, I don't think there is anyway to recover stuff on it from the previous filesystem!  I could be wrong which I hope I am so you can recover your files...

---

### Post by aspro on 2006-11-18
Not easily I'm afraid, you might be able to get your data back by getting someone who knows about forensically retrieving data of hard drives but thats far beyond myself to help you with.

---

### Post by koenn on 2006-11-18
If those files are really important - say, your company's bookkeeping or something - you should start lookingh for a decent data recovery firm. i've heard they're not cheap.

If those files are really, really important, you should have made a backup. Especially before changing partitions. Says so in every howto. Doesn't really help, does it ? And you're probably not the first one to go ahead with repartitioning without backup. I've done it several times myself. 

Long shot and entirely at your own risk:
If I was in such a situation, and the files ware not important enough to justify spending money on recovery, I'd try something like this:

1- partition again, in the original partitioning scheme 
2- put disk in a 2nd computer, so you can run data recovery software on it
(I've used ZAR before, it works - [http://www.z-a-recovery.com/](http://www.z-a-recovery.com/) - )
you may or may not have to format the partition once more (to NTFS)

The reasoning is as follows :
recreating the partition table tells the recovery software where to look or what to look for. Formatting does not fill the entire disk with data. Data that has not been overwritten yet, is still present on the disk and may be recoverable so you might get at least some files back.

Again, this is a long shot. It may make things worse, and if you're going to call in data recovery professionals, you better leave the disk alone and let them take care of it.

---

