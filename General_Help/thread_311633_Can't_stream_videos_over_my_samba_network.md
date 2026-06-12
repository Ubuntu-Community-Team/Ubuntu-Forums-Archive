---
title: "Can't stream videos over my samba network"
date: 2006-12-03
forum: General Help
---

### Post by k0rv3n on 2006-12-03
Hi.

I'm trying to change completely to ubuntu now, getting tired of windows fu**ing up all the time. But now I got kind of a problem in ubuntu.

I got a server with samba running on it. I can access the shares that I have set up and read i.e. pictures and pdf's directly over the network. But I can't stream videos from the server, instead I have to dl them localy and then play them. It worked fine in windows streaming the vids from the server.

The msg I get from Totem, when trying to start a vid is something like this:

```
Totem could not play 'smb://server/Share/[Lunar] Bleach - 01 [2101CD82].avi'.
Could not read from resource.
```

Anyone had the same prob and managed to solve it?

---

### Post by Joshua Hesketh on 2006-12-03
This is a bug that has come up in the latest version of Ubuntu. It is unfortunate, but an easy way around it is to use smbFS. To do this install smbFS:
```

sudo aptitude install smbfs

```
Now you can mount samba shares as local file systems.
```

#First create a directory to mount it in
sudo mkdir /media/samba_share
#now mount
sudo mount -t smbfs //computer_ip_or_name/share_name /media/samba_share

```
and that should work!. 

Let me know how you go, you can also set up your file system to mount samba shares on boot ;)

---

### Post by k0rv3n on 2006-12-03
> **Joshua Hesketh said:**
> This is a bug that has come up in the latest version of Ubuntu. It is unfortunate, but an easy way around it is to use smbFS. To do this install smbFS:
```

sudo aptitude install smbfs

```
Now you can mount samba shares as local file systems.
```

#First create a directory to mount it in
sudo mkdir /media/samba_share
#now mount
sudo mount -t smbfs //computer_ip_or_name/share_name /media/samba_share

```
and that should work!. 

Let me know how you go, you can also set up your file system to mount samba shares on boot ;)

Hey thanks man!!
Really fast reply.
It work smoothly.

How do you set up it to mount on boot?
is it in fstab?

---

### Post by k0rv3n on 2006-12-03
Yeah and also...

I have to be root to mount (sudo), so now I dont have permissions as my regular user to write to the mounted points.

Still a noob :-D

---

### Post by Marsolin on 2006-12-03
You can also use [Smb4K]("http://linuxappfinder.com/package/smb4k") to pick shared drives to mount. It will also remount on boot if you want.

---

### Post by Joshua Hesketh on 2006-12-04
This link here will provide some useful details on how to mount smb shares on boot, even with password protected shares ;).

[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

Hope that helps :)

---

### Post by k0rv3n on 2006-12-05
Thanks a bunch man!

---

### Post by jjrp78 on 2008-06-21
Hi guys,

This thread is old I hope you guys are still tunned. Im having this same problem with ubuntu hardy and the work around works fine but I dont wanna have to mount the share every time (im in a big network and allways streamming media from different servers) is there any other way? or perhaps using smbfs to mount shares on the fly ie by typing the smb://xxx address on a window (this is how I usually access the shares) how would I do that?

---

### Post by Jense on 2008-06-21
I have the same problem here. Just playing shares directly from the server worked fine in 7.4 and 7.10, but not in Hardy. I've been searching for quite some time but can't find a reason or solution to this. Please help!!

Thx

---

### Post by jjrp78 on 2008-06-23
aparently is a bug in the latest samba update:

[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/241448](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/241448)

I guess they will fix it some time soon

Update Jul 1 2008: Fixed install the latest updates (there should be some samba stuff there) and it will play again

---

