---
title: "Root drive full"
date: 2017-10-31
forum: General Help
---

### Post by rlongfield on 2017-10-31
Hey all.

I've installed a myriad of things over the years and I think time and poor un-installs have caught up with me. 

I am running Ubuntu 14.04.5 LTS and my / partition has run out of space.

Here is the breakdown of my system.
```
udev            991M     4.0K    991M   1%     /dev
tmpfs           201M     9.4M   191M   5%     /run
/dev/sda1     9.1G      8.6G    0        100% /
none            4.0K      0        4.0K    0%     /sys/fs/cgroup
none            5.0M     0        5.0M    0%    /run/lock
none            1001M   28M    974M   3%    /run/shm
none            100M    44K     100M   1%    /run/user
/dev/md0      1.8T     1.7T   101G    95%  /Media
/dev/sda6     218G     173G  35G      84%  /home
```
Is there a way of freeing up space on / or can I re-partition space from /home to / without killing everything? /home and / are physically on the same drive.

According to ncdu the biggest space users are:
```
/usr
/usr/lib
/usr/lib/x86_64-linux-gnu
/usr/lib/debug
/usr/lib/chromium-browser
/usr/share

/var
/var/lib (this is Plex which I just installed, and mythtv streaming that I need to clean up, that's another forum post)
/var/log
/var/cache
```
Thanks,
-Rob

---

### Post by oldfred on 2017-10-31
Your /home is also almost full. 
You should not get over 80-90%, with Windows anything over 70% or 30% free starts to slow system. And with Windows at 10% free you just about cannot do a defrag as there is no working room. Linux is not quite as restrictive, but you still need some space for system to work well. Ext4 partition even hides 5% to try to prevent you from filling drive and causing major issues.

Also a 9GB / partition is not very large even when you have a separate /home. 
I normally partition 25GB and have all data in a /mnt/data partition. And I have used about 12GB in / (root).

Have you deleted old kernels, old logs and other housecleaning?
       RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

 Caution deborphan will delete anything you manually installed. See comment: 
 Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.

---

### Post by ajgreeny on 2017-10-31
Your big disk-space user is possibly plex as both /usr/lib/plexmediaserver and more likely /var/lib/plexmediaserver may have a huge content, though of course, it depends on the amount of media that you are serving; I have about 500GB of media files to serve via plex and my /usr/lib/plexmediaserver contains about 256MB and /var/lib/plexmediaserver about 1.6GB.

I do not know the workings of plex setup well enough to know if you can move all that content to your /home where you have more space but it may be worth searching on the plex forum.
I do not know myth at all but that may also use large amounts of disk space so could be worth investigating.

---

### Post by meetdilip on 2017-10-31
Have you tried Stacer or Bleachbit to clean cache and related junk. ? It might help.

---

