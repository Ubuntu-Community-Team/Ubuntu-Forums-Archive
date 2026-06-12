---
title: "Hard Disk Help"
date: 2007-06-28
forum: General Help
---

### Post by Master Jedi on 2007-06-28
My computer has 3 hard disks in it:

Controller 1 (SATA):
- 80 GB Drive
- Controller is on the motherboard

Controller 2 (PATA):
- 200 GB Drive (contains kubuntu installation)
- 250 GB Drive (for MythTV recordings)
- controller is a PCI card


**USUALLY** the 200 GB drive shows up as sda, the 250 GB is sdb, and the 80 GB is sdc. Sometimes when I boot, the 80 GB drive becomes sda, the 200 GB drive is sdb, and the 250 GB drive is sdc.

My fstab contains the line:

/dev/sdb2 /media/sdb2 auto defaults 0 0

This mounts the partition on the 250 GB drive correctly, only when it is sdb.


How do I get this to behave consistently? The only solution I have so far is reboot until it works. I don't care what the designations of the disks are as long as the correct partitions are mounted to the correct locations at each and every boot.

---

### Post by Rui Pais on 2007-06-28
hi,
yes, thats a typical problem with mixed SATA/PATA.

Do: 
```
sudo vol_id -u /dev/sdb2
```
(or /dev/sdc2 if HD it's detected as sdc).
It should output the UUID of partition, long series of numbers and letters.

Copy the output and replace on fstab:
```
/dev/sdb2 /media/sdb2 auto defaults 0 0
```
with
```
UUID=XXXXXXXXXXXXXXXXXXXXXXX  /media/sdb2 auto defaults 0 0
```

that make it independent on how kernel see it.

hth

---

### Post by Master Jedi on 2007-07-05
Ftw \\:d/

---

