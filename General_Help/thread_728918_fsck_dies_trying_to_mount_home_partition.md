---
title: "fsck dies trying to mount home partition"
date: 2008-03-19
forum: General Help
---

### Post by Achetar on 2008-03-19
During bootup fsck dies trying to mount my /home partition. I recently deleted this partition to resize it to 15GB (formerly 5GB). Here is the log it creates:

```
Log of fsck -C3 -R -A -a
Wed Mar 19 09:48:00 2008

fsck 1.40.3 (05-Dec-2007)
fsck.ext3: Unable to resolve 'UUID=e4e02423-2bbc-49bd-9a65-b86bf53aa133'^M
fsck died with exit status 8

Wed Mar 19 09:48:00 2008

```

After it dies I hit Ctrl+D and boot into ubuntu hardy. Then I have to login to failsafe xterm and run 'sudo mount /dev/hda3 /home' and it works fine from there. Any help?

---

### Post by plucky on 2008-03-19
Achetar,

The **UUID** of the partition has changed because you resized it.
In Ubuntu open a terminal and type ```
blkid
``` and then ```
cat /etc/fstab
```.

This will show the home partition UUID is different.

To fix ```
gksudo gedit /etc/fstab
``` and replace the incorrect UUID  with the one you got from the **blkid** command using copy and paste.


Good Luck

---

### Post by Achetar on 2008-03-20
Perfect! Thank you!

---

### Post by gypaete09 on 2008-05-27
had the same problem, checked UUID's - were identical: fsck log:

Log of fsck -C -R -A -a 
Tue May 27 12:11:00 2008

fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sdb1: 83 files, 3696/24026 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sdb3: 1677 files, 582248/823724 clusters
fsck.ext3: No such file or directory while trying to open /dev/sdc1
/dev/sdc1: 
above stands for switched-off external usb disk :-)

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

/dev/sda2: clean, 201895/13615104 files, 9632910/27228166 blocks (check after next mount)
fsck died with exit status 8

Tue May 27 12:11:01 2008
----------------

This talks about a bad superblock ( sometimes the system boots up normally and mounts /dev/sda2, but more and more often I need to re-mount it myself.)
What can be done to repair / rewrite this superblock? is it what others call the master boot record or MBR?
(yes, sorry, I am an ex Novell and M$oft support, not really a mac or unix man...
Could it be that XP messes with the superblock when I boot XP? (that's very rare now)


Update: since /dev/sda2 got a forced check (did not dare to mess up a manual fsck..), the problem self-fixed, apparently.

This does not confirm Murphy's Law, for once ;-)

---

