---
title: "disk mounting question"
date: 2021-08-14
forum: General Help
---

### Post by jgw on 2021-08-14
I am trying to setup a new drive.  I have my old drive which I was having problems with.  My problem is that I am trying to also use the stuff on the old drive.  One of the problems is setting up older programs and putting the addresses of locations on another drive.  In this case the drive is currently at  /mnt/8ccdc8d0-afeb-4c4b-bb44-9b4e84b7ecd4  Before the new drive that same drive was known as /mnt/data.  I remember that I that location name to 'data' but can't remember how I did it.

I think I did it by just going to disks and changing the uuid from that long number to "data" but don't want to wreck my file system so I thought I had better ask first.

It just got better.  I went to files and then other locations and the drive was referred to, by files, as "data".  Just thought I would add that (for what its worth)

Thank you.............

---

### Post by TheFu on 2021-08-14
If you set the LABEL for a partition, that should be used under /media/{username}/{LABEL} for devices that aren't already known to the system.
We can also use the LABEL in the fstab to mount a file system.  Just use LABEL= instead of UUID= in that file. Obviously, the LABEL must be unique across all storage devices that may ever be connected to the system.

UUIDs aren't good for humans. LABELs are.

Of course, if you use more advanced storage solutions, then there are other ways to mount which can be even more clear to admins.

---

### Post by oldfred on 2021-08-14
I label all partitions, but some are only occasionally used, so they do mount using the label, in /media.
I have confused myself by labeling a partition Data, but mounting as /mnt/data. Those are two different mounts. Case is important in Linux.

But a data partition I want to use a lot, I mount with fstab in /mnt/data.
You have to create mount point, edit fstab and may have to change ownership & permissions.

[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by jgw on 2021-08-15
Thanks for the responses.

I continued to search and found a command, tune2fs, which does the job.  This is an amazing tool and one can do much with it, including, I suspect absolutely destroying your machine.  Here are a couple of links:
[https://www.cyberithub.com/13-useful-tune2fs-commands-to-manage-ext2-ext3-ext4-filesystem/](https://www.cyberithub.com/13-useful-tune2fs-commands-to-manage-ext2-ext3-ext4-filesystem/)
[https://manpages.ubuntu.com/manpages/xenial/man8/tune2fs.8.html](https://manpages.ubuntu.com/manpages/xenial/man8/tune2fs.8.html)

I will mark this a solved........

---

