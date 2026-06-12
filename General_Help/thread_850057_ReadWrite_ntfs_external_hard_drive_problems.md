---
title: "Read/Write ntfs external hard drive problems"
date: 2008-07-05
forum: General Help
---

### Post by sanjbmw2001 on 2008-07-05
Hi Everyone

I've a external hard drive formatted to ntfs.
I've read/write/access through Ubuntu 8.04
I also have opensuse 11 on the laptop.
Unfortunately while using opensuse 11 I do not have write permissions to the external hard drive.
Please could someone help me out.

---

### Post by Linux&amp;Gsus on 2008-07-05
I had trouble my external HD as well. I don't know if that is the exact same problem. But have a browse through here:
[http://ubuntuforums.org/showthread.php?t=848108]("http://ubuntuforums.org/showthread.php?t=848108")
Maybe it helps. Never know.

PS: What has that Poll to do with the topic at hand? :confused: Besides that there are many missing brands.
Anyways, don't need to understand everything. :)

---

### Post by sanjbmw2001 on 2008-07-06
The poll has got nothing to do with the questions:lolflag:

However my question remains.

The external hdd was installed with ubuntu with all the necessary permissions,I installed opensuse 11 later. whilst I can read the external hdd I cannot write to it "permission denied"
I require the external hdd to be accessible by both ubuntu and opensuse.

Help please.:(

---

### Post by caljohnsmith on 2008-07-06
It has to do with how the NTFS partition is mounted. Does Suse automatically mount the external HDD on startup? If it does, then just make sure the entry in the /etc/fstab for the NTFS partition on that drive has a "rw" option (read-write). For instance, here's how my NTFS partition is mounted in fstab:
```
UUID=68F0C561F0C5365A /media/sda1 ntfs defaults,umask=007,uid=0,gid=46,auto,rw,n
ouser 0 1
```
If Suse does not automatically mount it, you could use the "mount" command and then specify the -w option to make sure it is read-writable, although it should be read-writable by default if you use the mount command.

---

### Post by sanjbmw2001 on 2008-07-06
:KSThanks for all your help.

Actually I found the answer.


"In the terminal window type
su
[COLOR="Magenta"]enter your password[/COLOR]
mkdir /mnt/harddrive
mount -t ntfs-3g /dev/sdb1 /mnt/harddrive
chmod -R 777 /mnt/harddrive"


change /mnt/hardrive to the place where your external harddrive is mounted e.g. /media/Entertainment-1

:KS

---

