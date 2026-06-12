---
title: "Recover deleted files EXT4"
date: 2021-02-19
forum: General Help
---

### Post by anacorreia on 2021-02-19
[SIZE=2][FONT=arial]Hi,
I made a mistake, and rsynced with --delete.
How i can recover all the delete files? Please Help. This machine have my phd project and remove my work.

i use [/FONT][/SIZE]```
[COLOR=#000000][FONT=Menlo]testdisk /dev/vda1[/FONT][/COLOR]
```, select the disk,-> select NON Partitioned Media -> Advanced Filesystem Utilis 

I show [ATTACH=CONFIG]287982[/ATTACH] , In Option "LIST" i can see the delete files, but how can restores all delete files?
Thank you so much
[SIZE=2][FONT=arial]

[/FONT][/SIZE]

---

### Post by schragge on 2021-02-19
Is **cloudimage-rootfs** the partition where deleted files are? Is it the root partition of your system (the one that is mounted at **/**)?

 I'm asking because if not, you could install and use something like [extundelete]("https://manpages.debian.org/unstable/extundelete/extundelete.1.en.html") instead of **testdisk**.

Fot TestDisk, see [the explanation]("https://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_ext2") in their Wiki.

---

### Post by anacorreia on 2021-02-19
Hi, the [COLOR=#000000] [/COLOR]**cloudimage-root** is my root [COLOR=#000000]partition. 
This machine is a server.

[/COLOR]

---

### Post by schragge on 2021-02-19
Do you have a backup of deleted files?

---

### Post by anacorreia on 2021-02-19
No :(

---

### Post by ActionParsnip on 2021-02-19
> **anacorreia said:**
> No :(
Why do you not have backups? What if the IDE on your drive fails? Where is your data then?

---

### Post by anacorreia on 2021-02-19
You are right.  was very stupid.
Can i use extundelete -restore-all ?
do i need to repair the superblock??

because he show 

```
uperblock 0, blocksize=4096 [cloudimg-rootfs]
   ext4                   260   1  2 83478   4 60   83883992 [cloudimg-rootfs]
 superblock 0, blocksize=4096 [cloudimg-rootfs]
   ext4                   780   3  4 83998   6 62   83883992 [cloudimg-rootfs]
 superblock 0, blocksize=4096 [cloudimg-rootfs]
   ext4                  1300   5  6 84518   9  1   83883992 [cloudimg-rootfs]
 superblock 0, blocksize=4096 [cloudimg-rootfs]
   ext4                  1820   7  8 85038  11  3   83883992 [cloudimg-rootfs]
 superblock 0, blocksize=4096 [cloudimg-rootfs]
   ext4                  2340   9 10 85558  13  5   83883992 [cloudimg-rootfs]
 superblock 0, blocksize=4096 [cloudimg-rootfs]
    

superblock 0, blocksize=4096 [cloudimg-rootfs]
   ext4                  7021  11 28 90239  15 23   83883992 [cloudimg-rootfs]
 superblock 0, blocksize=4096 [cloudimg-rootfs]
   ext4                 12743   1 50 95961   5 45   83883992 [cloudimg-rootfs]
 superblock 0, blocksize=4096 [cloudimg-rootfs]
   ext4                 21065   2 19 104283   6 14   83883992 [cloudimg-rootfs]
 superblock 0, blocksize=4096 [cloudimg-rootfs]


 To repair the filesystem using alternate superblock, run
>fsck.ext4 -p -b superblock -B blocksize device   
```

---

### Post by oldfred on 2021-02-19
Never had to use it, but I thought if testdisk showed files, you from that listing could copy to another drive.
Best practice is to create a backup of the image to another drive, and only work on the image copy, so if you damage it, then you still have original.

Full image backup
GNU ddrescue (packaged as gddrescue, though once installed the command is "ddrescue") 
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://ubuntuforums.org/showthread.php?t=2305215&p=13401824#post13401824](http://ubuntuforums.org/showthread.php?t=2305215&p=13401824#post13401824)

---

### Post by anacorreia on 2021-02-19
Thank you so much, i will try do that

---

### Post by dragonfly41 on 2021-02-19
A few added points ..

Data recovery is a very lengthy process and might impact on your PhD project studies.
Try other methods before resorting to TestDisk. 
Note that installing extra software might overwrite the very files you are trying to recover.
Hence the advice above to clone your drive first as insurance plan. Stop using your PC.

If you launch GParted (partition editor) there is an option to try .. Device > Attempt Data Rescue

If you use testdisk it will list ***all ***deleted files including those historical files you chose to delete earlier

If you use testdisk you will require some device (additional space) where recovered files are placed. Not in the same device you are recovering.

Conclusion .. use testdisk with care, preferably running testdisk in a Live USB and not the device you are trying to recover.

[P.S.] There is a data recovery app named **R-Linux** which I would try installing in a LiveUSB instance and then use that to look for deleted files in your device.   I would prepare this LiveUSB on another PC if you have one to avoid using your existing PC.

> R-Linux is a file recover utility for the Ext2/3/4FS file system used in the Linux OS and several Unixes. R-Linux uses unique IntelligentScan technology and flexible parameter settings to give you real control over the fastest data recovery ever seen. It recovers files from existing partitions even when file records are lost. R-Linux is a lite version of more powerful file recover utility R-Studio. R-Studio utilizes the IntelligentScan technology to its full extent, and therefore can recover data from partitions with broken file systems. Also, R-Studio recovers data over network.

---

### Post by ActionParsnip on 2021-02-19
Remember. a 1Tb disk is dirt cheap and would enable you to recover data easily and quickly. Even a manual copy and paste every now and then is enough

---

### Post by HermanAB on 2021-02-20
Err... If you are working on a PHD (lots of invested time and effort), then you should take your PC to an expert data recovery company and not try to do it yourself.  The first thing you should do, is unplug it from the wall and stop using it, since using it, overwrites old erased files on the disk - the ones you want to restore.

---

### Post by TheFu on 2021-02-20
For the future, tools like **Back-in-Time** will take hourly snapshots (really rsync + hardlinks), then selectively remove those "snapshots" as time moves forward.  You'll have 48 hourly snapshots (the last two days), then 1 snapshot per day for the last week, then 1 snapshot per week for the last month, then 1 snapshot per month for the last year.  You get the point.  I may not be exactly correct, but there are definitely hourly snapshots created and selectively removed over time.  
Perfect for people doing important work daily that is kept in the HOME.  Back-in-Time wasn't so great for doing system backups, but for end-user files in a HOME directory, it wasn't bad.

Because these snapshots use hardlinks, the amount of storage needed for many snapshot versions is actually tiny.
I set this up for my Mom's system and she used it for a few years (RIP).

Having backups is much better than not having them and losing data, as you know.  Even better if that process is easily automated.

---

