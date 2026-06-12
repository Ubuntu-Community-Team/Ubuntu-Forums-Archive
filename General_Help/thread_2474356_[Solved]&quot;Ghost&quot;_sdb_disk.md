---
title: "[Solved]&quot;Ghost&quot; sdb disk"
date: 2022-04-27
forum: General Help
---

### Post by iutech on 2022-04-27
A Dell computer pre-installed with Ubuntu has two disks, one hard disk on /dev/sda and one SSD on /dev/nvme0*.
The system is on the SSD, and to the extent of my knowledge works well. 
The SSD is on vfat (for ESP and "OS") and ext4 (for Ubuntu).
The hard disk has no filesystem, so I wanted to format it, and to use lvm on it.

Everytime I make a lvm command (be it pvdisplay, pvs, pvcreate,  vgcreate) I get answers about /dev/sdb ("/dev/sdb: open failed : aucun  support trouvé") though I don't have any sdb on my system, only the sda  hard disk and the nvm* SSD...
  
Actually though lsblk shows only /dev/sda and /dev/nvme* (and a lot of /snap crap), lsblk --all do show a  /dev/sdb with no indication of size and the flag "removable" set to 1.
  
Why is that ? What could this ghost /dev/sdb be ?
Is there a risk of doing something dangerous and unexpected to the existing filesystem with my lvm commands since they seem to call /dev/sdb for whatever reasons ?

---

### Post by ActionParsnip on 2022-04-27
Can you give the output of:
```

pvdisplay; vgdisplay

```
Thanks

---

### Post by iutech on 2022-04-27
pv display :
```
 
  /dev/sdb: open failed: Aucun support trouvé
  /dev/sdb: open failed: Aucun support trouvé
  --- Physical volume ---
  PV Name               /dev/sda
  VG Name               Disque12To
  PV Size               10,91 TiB / not usable 4,00 MiB
  Allocatable           yes 
  PE Size               4,00 MiB
  Total PE              2861055
  Free PE               2861055
  Allocated PE          0
  PV UUID               ***-***-***

```

vgdisplay :
```
 
  /dev/sdb: open failed: Aucun support trouvé
  /dev/sdb: open failed: Aucun support trouvé
  --- Volume group ---
  VG Name               Disque12To
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  1
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                0
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               10,91 TiB
  PE Size               4,00 MiB
  Total PE              2861055
  Alloc PE / Size       0 / 0   
  Free  PE / Size       2861055 / 10,91 TiB
  VG UUID               *****-****-****

```

I did create lvm physical volume (with pvcreate /dev/sda) and volume group (with vgcreate Disque12To /dev/sda), but stopped there.

---

### Post by ActionParsnip on 2022-04-29
[https://forum.proxmox.com/threads/a-warning-dev-sde-no-medium-found-everywhere.57537/](https://forum.proxmox.com/threads/a-warning-dev-sde-no-medium-found-everywhere.57537/)

Can use a global filter to remove the disk. Should suppress the message. You can do this in /etc/lvm.conf

---

### Post by iutech on 2022-04-29
Thanks !
I did access physically to the disk today and /dev/sdb is clearly the slot for the SD card, the diod for it lighted every time I made a lvm command and shut off when I wasn't.
So indeed it's just a matter of creating a filter so it's not called when I do a generic lvm command.
Problem solved.

---

