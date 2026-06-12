---
title: "Mount points for fat32/ntfs partitions not remembered after log out."
date: 2006-11-06
forum: General Help
---

### Post by oobuntoo on 2006-11-06
Cannot access fat32/ntfs partitions when log out then log back in on Kubuntu Edgy fresh install. Reboot the system, and they are there again. Log out then log in, and they are gone. Bring up Hal-device-manager and check out partition mount points for these partitions and there are none.

This did not happen with the Ubuntu (Gnome) install. What is missing with Kubuntu?

I re-install Kubuntu the second time, and same sh*t happened. Anyone else has this issue? ](*,)

---

### Post by dbd on 2006-11-06
How are you mounting them? Are you mounting them manually using the command line? Because if so then that does not set them to mount next boot.

If you go into the KDE System Settings, Advanced section, then there is a tool to configure the mounting of other partitions. I can't remnember what its called, but I think its something like disks and file systems.

good luck!

---

### Post by taurus on 2006-11-06
What's your /etc/fstab look like then?

---

### Post by oobuntoo on 2006-11-07
No, I did not mount them manually. They are mounted by default just like in Dapper. I did not have to configure or change anything in fstab since Breezy. 

I'm not at home at the moment, so I can't post my fstab. I doubt it's my fstab that caused the problem. It works OK as long as I don't log out.

Like I posted above, the Ubuntu version install did not have this problem. I even compared the fstab files from the two installs and they look exactly the same for fat32/ntfs partitions.

---

### Post by dbd on 2006-11-07
Hmm, that is very strange, I have no idea why logging out and in again would cause them to no longer be mounted.

Does the command:
> sudo mount -a
mount all of the fat32/ntfs partitions after you log out and in again? Because you could set that to run everytime you log in if it does. Not really a very nice solution, but it may work.

I think is taurus right, it would probably be handy to see your fstab.

---

### Post by oobuntoo on 2006-11-07
Here is my fstab under Kubuntu:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=b2faf7b1-f8e5-4eff-8af9-b7bbf7b13854 /          ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=fc68ca3c-6230-4701-8d4a-1c5232ddf51b /home      ext3    defaults  0       2
# /dev/sda5
**UUID=5B16-C18C**  /media/audio    vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda1
**UUID=E0A8DDA9A8DD7E8A** /media/winxp    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
**UUID=58BD-B335**  /media/storage  vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
**UUID=B2AD-E7BE**  /media/video    vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=fd8818c3-e288-455c-9f68-72e63a7c6543 none            swap    sw   0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto    0    0            

```


and this is the fstab under Ubuntu:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=5ac12173-9eec-43e8-830f-fa5156724c92 /        ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=a15c921f-1ce8-40dc-86e3-db09e40e1ad2 /home    ext3    defaults    0       2
# /dev/sda5
**UUID=5B16-C18C**  /media/audio    vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
**UUID=58BD-B335**  /media/storage  vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
**UUID=B2AD-E7BE**  /media/video    vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda1
**UUID=E0A8DDA9A8DD7E8A** /media/winxp    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=60317e7d-13c1-4ab0-ba93-392689afe60e none            swap    sw   0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

For the fat32/ntfs partitions, they look exactly the same.

---

### Post by oobuntoo on 2006-11-07
I've managed to solve this problem. I've just gone back to the Dapper way of setting up fstab file.

That is, instead of this:
```
# /dev/sda5
UUID=5B16-C18C  /media/audio    vfat    defaults,utf8,umask=007,gid=46 0       1

```

change it to this:
```
/dev/sda5 /media/audio    vfat    defaults,utf8,umask=007,gid=46 0       1
```

I don't really know what "UUID=5B16-C18C" is really supposed to do, but it works jus fine under Ubuntu/Gnome but not Kubuntu. At least not for me.

---

