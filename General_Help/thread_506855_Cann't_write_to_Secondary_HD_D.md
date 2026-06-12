---
title: "Cann't write to Secondary HD D:\"
date: 2007-07-22
forum: General Help
---

### Post by RaigyCar on 2007-07-22
I have two HD installed on my machine, but i cannot write to my secondary HD D:\

I can read files from it but cannot write to it.

I posted a thread on the Installations & Upgrades forum here:

[http://ubuntuforums.org/showthread.php?t=506448](http://ubuntuforums.org/showthread.php?t=506448)

Since i installed Ubuntu with Wubi i thought it would be better asking for advice here.

Thanks in advance.

---

### Post by hh93 on 2007-08-26
quite some time since the last time you post, did you get any answer from wubi forum?

---

### Post by tuxcantfly on 2007-08-26
Maybe try:

sudo mkdir /media/vfat
sudo mount /dev/sda2 -t vfat -o-o iocharset=utf8,umask=000 /media/vfat

And can you access it r/w as root?

If you need a more detailed guide, try this:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite)

And if you want it on bootup:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by tuxcantfly on 2007-08-26
Also, I'm assuming your drive is not the host, and is vfat not ntfs, if it's the host, you should be able to access it through /media/host and if it's ntfs, see the guide I linked to in my previous post

---

### Post by Diabolis on 2007-08-26
You have to change permissions on your mount point. For example, if you are mounting your partition in the folder /media/fat32, then you have to do this:
```
sudo chown username /media/fat32
```

You have to do this **before** you mount your partition.

---

