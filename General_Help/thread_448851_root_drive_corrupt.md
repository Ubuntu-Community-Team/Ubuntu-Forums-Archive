---
title: "root drive corrupt"
date: 2007-05-19
forum: General Help
---

### Post by whistl3r on 2007-05-19
Half an hour back, Ubuntu got stuck, it could not recover from sleep, so I rebooted it using the power key. Upon restarting, I didnt look properly but it gave me some sort of a console, it said ramfs or something like that. I restarted again, but now GRUB gave me error no. 17. I restarted it again it gave me that same error so I booted using a live disk from where i am logged in right now. 

I tried to install grub using grub-install but it gave me a permission denied error. I opened gparted and saw the problem, it doesnt recognize my linux partition, there is an exclamation mark next to it and shows "unknown" for the filesystem type.

I tried using fsck, 

> $ sudo fsck -t ext3 /dev/sd6
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: No such file or directory while trying to open /dev/sd6

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo e2fsck -b 193 /dev/sda6
e2fsck 1.40-WIP (14-Nov-2006)
e2fsck: Bad magic number in super-block while trying to open /dev/sda6

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


Even if i can just recover files in my home folder it would be good.

---

### Post by confused57 on 2007-05-19
Maybe this link will help:
[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)

If you have access to another computer, you could burn a copy of  the gparted live cd, which can do a filesystem check, as described in the above link.

---

### Post by whistl3r on 2007-05-20
well i just ran fsck without the -t ext3 and it gave me loads of prompts to press y, after getting tired of pressing the y keys. I just refreshed gparted and it showed the partition correctly. But i think fsck was actually also deleted some files so i quit pressing y...
I rebooted to vista backed up my home folder and now I am reinstalling ubuntu.

sudo fsck -t ext3 /dev/sd6

---

