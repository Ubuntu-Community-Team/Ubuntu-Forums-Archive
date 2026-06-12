---
title: "Mount volume with mdadm"
date: 2012-10-22
forum: General Help
---

### Post by PrinzLangweilig on 2012-10-22
Hi,

I've got a RAID5 System with mdadm.

How can i mount it via command (with gui it is easy doubleclick)?
[PHP]
qcons@014-QCONS:~$ vim /etc/mdadm/mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#
ARRAY /dev/md0 metadata=1.2 spares=1 name=014-QCONS:0 UUID=d7a3a2b6:af5a5daf:f1a6b5a1:c043b52d

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers
DEVICE /dev/sd[bcd] /dev/sgk

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes


# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers
DEVICE /dev/sd[bcd] /dev/sgk

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR bln.schade@gmail.com
MAILFROM raid@qcons.de


[/PHP]

---

### Post by lrgmmc on 2012-10-22
Do you want it mounted at boot? If so add /dev/md0 to /etc/fstab.

---

### Post by PrinzLangweilig on 2012-10-29
how do i do this?

---

### Post by lrgmmc on 2012-10-29
add this to the bottom of fstab. 

```
sudo nano /etc/fstab
/dev/md0  /media/raid  ext4 defaults 0 0
```
now thats a basic setup. If you're not using ext4 change that to the file system you're using. Same with /media/raid change that to where you want it mounted.

---

