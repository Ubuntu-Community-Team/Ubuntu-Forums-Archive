---
title: "Yet anothe file-system debacel: help please."
date: 2007-10-06
forum: General Help
---

### Post by infinitelink on 2007-10-06
Well...I have a Fat32 partition on which I can access and read/write to and from and mod files in some of the files/folders, but not others...

It says the owner is root, but even root won't write. : ( 

So here's the deal: I don't want to deal with all the "you can try", "mod etc/fstab" etc. which rarely works. Neither re-mount under HOME as some have done (especially since I have no idea how).

I simply want a way to force, system-wide, the system to recognize the partition and all on it as my property: AND to let me change the permission from the properties as root (which when I try it reverts and gives me one of those darn messages again).

Also, let's start a poll to ask Ubuntu to take time and actually fix bugs and dumb ever-persisting errors as fundamental as these: every time I use Ubuntu this never stops. If it wants to be adopted more this kind of thing just shouldn't ever show up period; on a Window's system it's possible to set file-permission etc...but you know what? Even in large, networked, environments I've never ever encountered anything like this, nor do I know anyone who ever has while they're working between businesses etc.. 

This is a simple basic that needs fixing. Who agrees?

---

### Post by dcstar on 2007-10-06
> **infinitelink said:**
> Well...I have a Fat32 partition on which I can access and read/write to and from and mod files in some of the files/folders, but not others...

It says the owner is root, but even root won't write. : ( 

So here's the deal: I don't want to deal with all the "you can try", "mod etc/fstab" etc. which rarely works. Neither re-mount under HOME as some have done (especially since I have no idea how).

I simply want a way to force, system-wide, the system to recognize the partition and all on it as my property: AND to let me change the permission from the properties as root (which when I try it reverts and gives me one of those darn messages again).

Also, let's start a poll to ask Ubuntu to take time and actually fix bugs and dumb ever-persisting errors as fundamental as these: every time I use Ubuntu this never stops. If it wants to be adopted more this kind of thing just shouldn't ever show up period; on a Window's system it's possible to set file-permission etc...but you know what? Even in large, networked, environments I've never ever encountered anything like this, nor do I know anyone who ever has while they're working between businesses etc.. 

This is a simple basic that needs fixing. Who agrees?

Possibly very few, because a lot of us use FAT32 partitions with no problems whatsoever.

There will always be issues with filesystems on different operating systems, you can have directory/filenames which are legal under DOS/Windows but won't work in Linux, and vice-versa.

If you have a problem, post the specific details and allow people to actually help you.

---

### Post by bodhi.zazen on 2007-10-06
> **infinitelink said:**
> So here's the deal: I don't want to deal with all the "you can try", "mod etc/fstab" etc. which rarely works. Neither re-mount under HOME as some have done (especially since I have no idea how).

Well, the problem is fat/ntfs partitions do not support permissions. Have you contacted Microsoft ?

So, to fix this you have to set ownership and permissions at the time of mount, and edit fstab.

Lucky for you there is an easy way, ntfs-config

Install ntfs-config any way you like, then open a terminal and enter ;


```
gksu ntfs-config
```

simple.

[http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

I know you often hear ntfs-config in association with ntfs partitions, but it also works on the fat ones, which in linux are vfat :twisted:

---

