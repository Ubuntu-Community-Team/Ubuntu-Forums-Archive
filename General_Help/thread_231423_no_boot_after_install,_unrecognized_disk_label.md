---
title: "no boot after install, unrecognized disk label"
date: 2006-08-07
forum: General Help
---

### Post by ghee22 on 2006-08-07
I moved this thead from installation help because I am not trying to install Ubuntu.  my problem now is data recovery, not installing ubuntu.  I copied and pasted thread below:

I started out the install with the livecd of dapper by choosing the option to automatically use free space. This came back with an error, so i closed out the installer program and reran it. Then the option to use free space was not there, but manual was. I chose manual.

I removed free space from my windows ntfs partition and created an extended partition for ext3 for root (about 4 gigs) and 1 gig for swap.

The install completed successfully and i rebooted. Then i get a no hd to boot from. i put back in the live cd and my ntfs partition (including the extended partition i made from its free space is one big fat UNKNOWN.

I am really freaking out because I didn't back up my documents. A very novice error, please please if anyone can help, i'm desperate.

Thanks.

---

### Post by vadaim on 2006-08-07
Have you tried [this]("http://ubuntuforums.org/showthread.php?t=24113&highlight=rewriting+mbr")? It may not be the solution, but it does not affect your 'unbackuped' data, and you can rescue the installed system to get your old files back.

---

### Post by ghee22 on 2006-08-07
> **vadaim said:**
> Have you tried [this]("http://ubuntuforums.org/showthread.php?t=24113&highlight=rewriting+mbr")? It may not be the solution, but it does not affect your 'unbackuped' data, and you can rescue the installed system to get your old files back.
I don't know where to after the manual partition step.
The partition, /dev/hda2, comes up as unknown.  i split hda2 during the install by removing 5 gigs of free space of the ntfs partition and created an extended partition from it (1 ext3 for /, 1 1.0 gig swap).

I don't want it to recognized as ext3 and i have no other partitions to choose as ext3.

is there a way i can just label this complete partition as ntfs?

---

### Post by ghee22 on 2006-08-07
```
sudo fdisk /dev/hda2
p

Disk /dev/hda2: 35.9 GB, 35969149440 bytes
16 heads, 63 sectors/track, 69694 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

     Device Boot      Start         End      Blocks   Id  System

Command (m for help):
```

---

### Post by ghee22 on 2006-08-08
^^^ bump ^^^

how about someone have an idea of imaging the drive so i can use the laptop?

---

### Post by ghee22 on 2006-08-08
parted
ran a check 1 on /dev/hda
Got following:
Warning: File system doesn't have expected sizes for Windows to like it.
Cluster size is 2k (1k expected); number of clusters is 24026 (47959 expected);
size of FATs is 94 sectors (188 expected).

---

### Post by ghee22 on 2006-08-08
If i try to boot my dell inspiron 700m, i get a Loading PBR for descriptor 2...done.
Bad PBR

then it hangs

---

### Post by ghee22 on 2006-08-09
i went to a data recovery center.  anyone know how to fix this, yet?

---

