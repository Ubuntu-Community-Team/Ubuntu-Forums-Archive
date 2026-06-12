---
title: "Permission denied with hfsplus partition"
date: 2006-12-06
forum: General Help
---

### Post by xoai on 2006-12-06
I used this to mount my hfsplus partition

```
sudo mount /dev/sda2 /mnt/mac -t hfsplus
```

And it works fine but there are some problems. I can not access some folders because of permission denied. For example if I want to use xmms to play music from a permission denied folder in hfsplus partition I have to use with root account. Does anybody know how to solve this problem?

---

### Post by bradleyd on 2006-12-06
try 
sudo mount /dev/sda2 /mnt/mac -t hfsplus umask=000

---

### Post by xoai on 2006-12-06
It does not work. I think umask doesnt work with hfsplus

---

### Post by bradleyd on 2006-12-06
have you tried sudo mount /dev/sda2 /mnt/mac -o rw -t hfsplus

---

### Post by bradleyd on 2006-12-06
look here  [http://www.penguin-soft.com/penguin/man/1/hpmount.html]("http://www.penguin-soft.com/penguin/man/1/hpmount.html")

---

### Post by xoai on 2006-12-06
I searched and found out hfsplus. But it seems only to be a driver. About hpmount I see someone report about crashed HD with this tool T.T

It is okie with every folder but folder in /mnt/mac/Users/MyUsername
If I login with root account I can access those folders.

---

### Post by xoai on 2006-12-07
Does anyone know how to solve this problem :( I can not access tons of documents and music, movies,..... I dont want to reboot to Mac OS each time I need something.

---

### Post by thorix on 2006-12-10
> **xoai said:**
> Does anyone know how to solve this problem :( I can not access tons of documents and music, movies,..... I dont want to reboot to Mac OS each time I need something.

I’ve just installed a HFS+ drive with all my music on an Ubuntu box. My problem is getting this properly shared into my Mac network via NFS (btw. Netatalk did the trick, but … this is a matter for another thread).

First of all HFS+ works with users, groups and permissions like UNIX, Linux and Ubuntu as well. Each user/group is identified by a number.
If you are the Mac user “xoai” with user id 501, you might be the Ubuntu user “xoai” with uid 1000. So accessing distinct locations might be allowed for user 501 (xoai on Mac), but not for user 1000 (xoai in Ubuntu).

In Mac OSX you could change the permissions to “free for everyone”, then you will be able to r/w from Ubuntu.

The harder route to success is synchronizing user’s nicks, uid’s and gid’s.

---

