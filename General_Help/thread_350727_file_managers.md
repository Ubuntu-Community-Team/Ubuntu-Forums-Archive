---
title: "file managers"
date: 2007-02-01
forum: General Help
---

### Post by mgame2k on 2007-02-01
I was wondering what Linux file manager application would allow my to view my files on my win xp drives. It uses ntfs format.

---

### Post by BIGtrouble77 on 2007-02-01
They will all allow you to see an NTFS drive, you just need to properly mount the drive.  Here's some info on the subject:
[http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only)

Here's the Edgy version:
[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only)

---

### Post by aktiwers on 2007-02-01
On both Dapper and Edgy my NTFS got mounted automaticly?

---

### Post by BIGtrouble77 on 2007-02-01
If you want it to mount the drive properly everytime you boot you should edit fstab like this:
```
sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab

/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0
```

Before you do this, run Gparted ( System -> Administration -> Gnome Partition Editor ) and find out what drive is your ntfs drive.  The example above assumes it's hda1.

---

