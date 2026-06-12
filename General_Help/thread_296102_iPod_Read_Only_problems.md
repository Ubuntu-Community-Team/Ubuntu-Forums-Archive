---
title: "iPod Read Only problems"
date: 2006-11-09
forum: General Help
---

### Post by John Whitmore on 2006-11-09
Hello all,
    Can't seem to find what my problem is here with my iPod. I've been using it for ages on Ubuntu and never had a problem before but this morning it's gone funny and does no want to change.

Firstly what I'm doing, and have been doing for a long time, is using my iPod as an extra external hard drive. That has never been a problem and I keep a backup of my data on the iPod so that I can move it from machine to machine. Basically my Ubuntu is the master Data and occasionally I update the iPod with "cp -r -u Data /media/ipod" 

That has been working for ages but now this morning I can't do this as it says that the iPod is a read only file system. What changed in the last week? 

My /etc/mtab file says:

/dev/sda2 /media/ipod vfat rw,nosuid,nodev,quiet,shortname=mixed,
uid=1000,gid1000,umask=077,iocharset=utf8 0 0

So it looks to me like it's read write. If I list the directory properties it says that I'm the owner and have read, write and execute permissions but not even root can write to it as it's a Read Only File System. 

Last computer I used it on was an Ubuntu lap top so maybe it's fried it's head or something?

I did search for an answer to this problem but have had no joy.

John

---

### Post by John Whitmore on 2006-11-09
Initial poster here again moved to another Ubuntu machine and it's working fine. Don't know what's happened the machine that I always use.

---

### Post by basse1989 on 2006-12-01
I have the same problem with my ipod.
I did a fresh dapper install and upgraded to edgy and now I cant write to my pod.
I am the owner of all the files and folder and have read/write access but still can't write to it...
my /etc/mtab is he same as yours
```
/dev/sdc2 /media/ipod vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
```

Anyone know anything about this?

---

### Post by basse1989 on 2006-12-01
paul20111 wrote this on [http://ubuntuforums.org/showthread.php?t=114402&page=2](http://ubuntuforums.org/showthread.php?t=114402&page=2)
```
sudo dosfsck -a /dev/sda2
```

and it fixed it for me :))

---

### Post by PrairieShaman on 2007-02-21
i did this but my ipod mounts to /dev/sdb3

this does not work for me, it's still read only. i just got this damn thing and now I cant use it. :( 

help please... 

Ive been scouring the internet with no help

---

### Post by Glendon on 2007-02-22
This helped me out. 

Ubuntu forums, as always, rock!

---

