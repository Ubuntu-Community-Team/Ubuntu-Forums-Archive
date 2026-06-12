---
title: "fstab and executable programs"
date: 2012-11-08
forum: General Help
---

### Post by bizkyt on 2012-11-08
Hello,

I want to mount a ntfs data partition, that I use on both ubuntu/windows. This is the entry that I added to /etc/fstab:

```
UUID=201702B70166AA54 /media/pedro/data ntfs-3g defaults,uid=pedro,gid=pedro,dmask=002,fmask=113 0 0
```

The partition mounts right every time I boot, but I can't change permissions of any file. Per example I want to run a executable program from command line and it gives: "bash: ./emissor: Permission denied", even if I give "chmod +x emissor", or trying from nautilus as in the image bellow:

[IMG]http://img688.imageshack.us/img688/1557/capturadeecrade20121108.png[/IMG]

If I click on the checkbox, it automatically unchecks..

What am I doing wrong?

---

### Post by hwttdz on 2012-11-08
There's a good explanation of dmask and fmask here:
[http://askubuntu.com/questions/113733/how-do-i-correctly-mount-a-ntfs-partition-in-etc-fstab](http://askubuntu.com/questions/113733/how-do-i-correctly-mount-a-ntfs-partition-in-etc-fstab)

After looking at it for 30 seconds, it seems you get to pick _one_ file and _one_ directory permission for the ntfs partition.  So chmod will never effect anything.  This seems like a good reason to avoid ntfs, but if you have to use it you have to use it.  Note that windows can also read fat32 (I'm not sure if that one is better).

---

### Post by oldfred on 2012-11-08
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

See also example from Morbius1--------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)

---

### Post by bizkyt on 2012-11-08
So to execute programs from that mount I have to use this?

```
UUID=201702B70166AA54 /media/pedro/data ntfs-3g defaults,uid=1000,gid=1000,**umask=022** 0 0
```

I was using this before, but it's annoying that every time I click to open per example a file.c, it prompts to execute/read/etc. I can't use a ext partition because this is my data partition and have to use it on both windows/ubuntu.

---

