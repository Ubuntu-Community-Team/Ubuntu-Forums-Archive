---
title: "help expanding partition size in 18.04"
date: 2019-01-26
forum: General Help
---

### Post by double_tap on 2019-01-26
I used a duplicator to copy the HD on my Ubuntu 18.04 box.  The old drive was a 160gb drive, and the new one is a 500g.  Can this partition be expanded to use the space?

thanks!

sudo parted -l
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End    Size   Type     File system  Flags
 1      1049kB  160GB  160GB  primary  ext4         boot

---

### Post by oldfred on 2019-01-26
You should just be able to use gparted from live installer.
You cannot change mounted partitions, so gparted will not work in your install.

---

### Post by double_tap on 2019-01-26
Thank you!  worked perfectly

sudo parted -l
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start       End       Size     Type     File system  Flags
 1          1049kB  500GB  500GB  primary    ext4            boot

---

### Post by oldfred on 2019-01-26
Glad it worked.
You can change to [Solved]

---

