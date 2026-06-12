---
title: "Disk errors on boot / mount"
date: 2013-10-27
forum: General Help
---

### Post by ottadini on 2013-10-27
I seem to be having some problems with my drives not shutting down cleanly. Can someone help me identify and fix the problem?

The error message I can see in kern.log is:
```
EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
```
Noting that sda2 is my / (root). 

Symptons include occasional boot and OS load problems (system freezing during boot, or on loading desktop), disk errors showing (inodes being deleted):
```
Oct 23 08:04:36 brick kernel: [    2.817994] EXT4-fs (sda2): INFO: recovery required on readonly filesystem
Oct 23 08:04:36 brick kernel: [    2.818115] EXT4-fs (sda2): write access will be enabled during recovery
Oct 23 08:04:36 brick kernel: [    3.094047] EXT4-fs (sda2): orphan cleanup on readonly fs
Oct 23 08:04:36 brick kernel: [    3.123264] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 528801
Oct 23 08:04:36 brick kernel: [    3.127215] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 791772
Oct 23 08:04:36 brick kernel: [    3.127296] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 791770
Oct 23 08:04:36 brick kernel: [    3.127348] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 791705
Oct 23 08:04:36 brick kernel: [    3.175285] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 788952
Oct 23 08:04:36 brick kernel: [    3.175320] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 788899
Oct 23 08:04:36 brick kernel: [    3.184290] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 788451
Oct 23 08:04:36 brick kernel: [    3.184322] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 788437
Oct 23 08:04:36 brick kernel: [    3.184350] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 788270
Oct 23 08:04:36 brick kernel: [    3.184373] EXT4-fs (sda2): 9 orphan inodes deleted
Oct 23 08:04:36 brick kernel: [    3.184414] EXT4-fs (sda2): recovery complete
Oct 23 08:04:36 brick kernel: [    3.246300] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
```

my /etc/fstab is:

```
proc            /proc           proc    nodev,noexec,nosuid 0       0

# / was on /dev/sda2 during installation
# /boot was on /dev/sda1 during installation
# /home was on /dev/sda6 during installation
# swap was on /dev/sda5 during installation

UUID=e7972335-1344-4ff8-b4cf-e4b70d2cb8cd /               ext4    errors=remount-ro 0       1
UUID=959fa271-d1d1-4eef-ba14-30e2837a6eea /boot           ext4    defaults        0       2
UUID=c1f3c3f6-5999-4357-8142-c747ed8beb15 /home           ext4    defaults        0       2
UUID=d28d2d75-fc02-41b1-be8e-5a8fa2011e35 none            swap    sw              0       0

# dingo (/dev/sdc1) is the 2TB drive
UUID=003ABB1739377B81  /mnt/dingo  ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,locale=en_AU.utf8  0  0

# data is /dev/sdb8
UUID=146FA9B0B6A44D89  /mnt/data  ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,locale=en_AU.utf8  0  0
```

I also see (on screen) some words to the effect that unmounting is throwing an error... but I have no idea where to see that in logs.

---

### Post by oldfred on 2013-10-27
I might try a full fsck on all ext4 partitions. May be a good idea to run chkdsk from a Windows repairCD on all the NTFS partitions also.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

How are you shutting down. If forcing reboot, change to REISUB.

      
 Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by ottadini on 2013-10-27
> **oldfred said:**
> I might try a full fsck on all ext4 partitions. May be a good idea to run chkdsk from a Windows repairCD on all the NTFS partitions also.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

How are you shutting down. If forcing reboot, change to REISUB.

      
 Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

Will try fsck later (when I finish for the day). 

REISUB: I always remember it as BUSIER backwards.

---

### Post by ottadini on 2013-11-11
I have run fsck and e2fsck a few times and each time there are no problems reported. 
I am shutting down normally, just via system menu, and the machine seems to shut down normally, though I don't know how to check that! Which log will tell me more?

Any help?

---

### Post by oldfred on 2013-11-11
I do not know what log file to look at. I normally only look at dmseg for booting.
       gksudo gedit /var/log/dmesg

But there are many log files and folder in /var/log

---

### Post by ottadini on 2013-11-20
Anybody got any ideas?

---

### Post by daniele3 on 2013-11-23
Same problem here, kernel 3.12.0-031200-generic, ubuntu 13.10 ----   fsck.ext4 -f on the root  filesystem yields no errors.

---

### Post by oldfred on 2013-11-23
@daniele3
Run the full fsck as in post #2. A simple fsck only checks to see if any issues have been reported and then may do something. The full fsck runs the full review.

---

### Post by ottadini on 2013-11-23
> **daniele3 said:**
> Same problem here, kernel 3.12.0-031200-generic, ubuntu 13.10 ----   fsck.ext4 -f on the root  filesystem yields no errors.

I am still hoping someone can provide a few hints to at least troubleshoot the problem. Please let me know here if you find help somewhere else.

---

