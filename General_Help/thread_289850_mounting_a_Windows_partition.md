---
title: "mounting a Windows partition?"
date: 2006-10-31
forum: General Help
---

### Post by tmarsh on 2006-10-31
I want to mount my Windows partition, but I can't find it in Places>Computer or in media.  It was listed there in 6.06; but I can't find it anywhere in 6.10.

---

### Post by electricshoes on 2006-10-31
If you open a terminal do

```
sudo fdisk -l
```See if there are any NTFS Devices listed here. 
If so, they can be added to your fstab.

```

/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0
```

Or whatever device your windows drive is.

You can also install NTFS write support with fuse
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

---

### Post by matthewstory on 2006-10-31
i would just add, that you should only edit your fstab if you want it to be mounted at system start up everytime.  If you only want to mount it as the need arises you only need to use the mount command:

mount /dev/hdaX /mount/point

Though I believe ubuntu mounts your windows partition automatically anyway, and so the need for either of these is kind of mute.

---

### Post by electricshoes on 2006-11-01
true. tmarsh-  if it is auto-mounting it should show up in /media/ See if you have it in there. Otherwise you can mount it like mathewstory said.

---

