---
title: "[SOLVED] Personal problem with volume permissions"
date: 2007-12-03
forum: General Help
---

### Post by ferdostar on 2007-12-03
Hi everyone!
Ok, here is my "little" problem:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda6
UUID=c5353c20-126a-436d-b9e3-54407a84c8ac     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sda1
UUID=473A-008D       /media/host0       vfat         defaults      0   0
/dev/hda7  none  swap  sw  0 0
```
The sda6 is my file system, the sda1 is a FAT32 partition, wich is mounted automaticly
The problem is that I can't change the read/write permissions on sda1 and respectively I can't mount/unmount the drive (except beeing root in a terminal, otherwise is telling me that I'm not privileged to mount the volume).
In fact, I've been searching on the forum, and trying differents things like:
1) First of all I tried to manage the volume with nautilus, but unfortanetly beeing root I couldn't change the permissions (it said that I'd not the permission to do that) ON BEEING ROOT! :confused: 
2) Second I tried  to add umask=000 at the fstab, but there was the same issue
3) Third I try to change the UIID by the username and it worked. I mounted the volume, but I couldn't see what there was in the drive (it was mounting /dev/hda1 and not /dev/sda1 (host0 in my case)).

I've searched also for some similar cases, like:
[http://ubuntuforums.org/showthread.php?t=478739](http://ubuntuforums.org/showthread.php?t=478739)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)   
[http://www.linuxforums.org/forum/misc/53527-cant-change-permissions-mounted-fat32-partition.html](http://www.linuxforums.org/forum/misc/53527-cant-change-permissions-mounted-fat32-partition.html) and so, but no results :(
So if anybody has some ideas and can help I'll be glad :)
Thanks in advanced!
Using Linux 2.6.20-15-generic Ubuntu 7.04 Feisy Fawn

ps: sorry for my english :)

---

### Post by el_rico on 2007-12-03
What do you mean by that you cannot change r/w permissions on /dev/sda6? 

Also, since it is your root FS, I do not see any reason to add 'user' in the fstab options. And actually I do not see any reason to umount it...

Can you give us more details?

---

### Post by ferdostar on 2007-12-03
Wow, thanks for the quick reply!
In fact I want to change the read/write permissions, cause I can't read or write on my volume :( So I tried to add other user, and giving him permissions. You're right I don't have any special reason to unmount the volume, but it's strange that I can't :confused:

---

