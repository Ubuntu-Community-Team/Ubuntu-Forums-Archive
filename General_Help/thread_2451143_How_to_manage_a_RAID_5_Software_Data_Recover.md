---
title: "How to manage a RAID 5 Software Data Recover"
date: 2020-09-28
forum: General Help
---

### Post by giobaxx on 2020-09-28
Hello to everyone

i need to replace all the disk in a workstation with a RAID 5 Software Configuration but  i want to keep it safe in case we would need to remount to recover some data. 

Due to the fact that is a Software RAID:


[LIST]
[*] I need to remount the 3 DISK in the same slot where were mounted before  or i just need  to remount the 3 disk regardless of workstation model and slot number?
[/LIST]

This, eventually to mark the disk with some label with useful information that could help me to re-mount the disk in the future in a correct way.

Thanks in adavence for the help

---

### Post by ActionParsnip on 2020-09-28
Make a backup to a different disk so there is no "recovery", you'd just restore the data from backup. A cheap USB drive will do this just fine.

---

### Post by giobaxx on 2020-09-28
I already did a backup running an rsync over another workstation, however they told to remove the disks and keep it safe in case we need it and i would like to know how i have to manage the three disks if i need to re-mount them and make it readble.

---

### Post by SeijiSensei on 2020-09-28
I would destroy the existing RAID 5 configuration, then rebuild it from scratch with mdadm.  My usual steps:

1) Use fdisk to create single partition on each drive that spans the entire device; use the T command in fdisk to mark each partition as type "fd - Linux RAID Autodetect"

2) Use mdadm to create the array, in your case something like
```
sudo mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdd1
```

3) Format the array as ext4.
```
sudo mkfs -t ext4 /dev/md0
```

4) Mount the array device and add a line to /etc/fstab to mount it automatically at boot.

---

