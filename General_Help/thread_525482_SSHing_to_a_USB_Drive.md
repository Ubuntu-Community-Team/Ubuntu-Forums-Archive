---
title: "SSHing to a USB Drive"
date: 2007-08-14
forum: General Help
---

### Post by zoba on 2007-08-14
I'm trying to access my USB drive on my Ubuntu install at home.  When I try to ls /media/FreeAgent Drive I get:

christopher@christopher-desktop:~$ cd /media/
christopher@christopher-desktop:/media$ cd FreeAgent\ Drive/
christopher@christopher-desktop:/media/FreeAgent Drive$ ls
ls: reading directory .: Input/output error


I'm not sure what to do. Thanks!

---

### Post by hkibak on 2007-08-14
I believe I have a similar issue.  I have a Sansa C 140 mp3 player that is essentially a USB drive.  When I connect it to my Ubuntu Feisty install at home I can see a few of the files under /media/Sansa c140$ but most of the files are truly invisible.  ls -a does not reveal them.  It is almost as though 95% of the drive (player) is in a partition that Ubuntu can't see.  I can write files to the player and copy files from the player.

I am able to migrate files back and forth on my other usb flash drives between my windows machine at work and my ubuntu machine at home... it is only my mp3 player that has this problem.

---

### Post by creedog on 2007-08-14
First off -- you are not sshing you are cd'ing.

Try cd'ing to a directory on the drive and doing a df -k . 
dont forget the .
reply with the output

```
christopher@christopher-desktop:~$ cd /media/
christopher@christopher-desktop:/media$ cd FreeAgent\ Drive/
df -k .

```

---

### Post by hkibak on 2007-08-14
I'm guessing that he meant that he is sshing into his machine at home and then trying to access the usb drive.

In my case df -k . returns the following:
Filesystem   1K-blocks      Used Available Use% Mounted on
/dev/sdb1       996672    922000     74672  93% /media/Sansa c140

---

### Post by zoba on 2007-08-15
I will try the df -k . at work today, though I'm not exactly sure what it is supposed to do I'll look it up.  Also, when I'm on my ubuntu install at home I can view all the files on my external drive just fine.

---

### Post by creedog on 2007-08-15
> **zoba said:**
> I will try the df -k . at work today, though I'm not exactly sure what it is supposed to do I'll look it up.  Also, when I'm on my ubuntu install at home I can view all the files on my external drive just fine.

the df -k . will run the disk free command on "." or what is known as your current directory. If you are on the directory/mount point for the usb disk then you will be able to tell from the output. If the disk is not mounted then you will be on the root disk and the output of that command will show that.

---

### Post by creedog on 2007-08-15
here is an example 

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1             35278540   3315480  30171012  10% /

```

This is the output from df -k . while in a directory that is on my root disk, note that its mounted on / 

now look at this below. this is the output from df -k . while in /media/disk

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc1             40126288  10243552  29882736  26% /media/dis
```


Note that now I am on a different disk and it has a different mount point.

---

