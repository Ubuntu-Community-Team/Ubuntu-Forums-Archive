---
title: "Mount volume via command (mdadm)"
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

### Post by Cheesemill on 2012-10-22
First create a directory where you want to mount it, for example:
```
sudo mkdir /mnt/data
```
Then use the mount command:
```
sudo mount /dev/md0 /mnt/data
```

---

