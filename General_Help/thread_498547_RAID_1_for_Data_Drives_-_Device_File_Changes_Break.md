---
title: "RAID 1 for Data Drives - Device File Changes Break Array"
date: 2007-07-11
forum: General Help
---

### Post by sshapiro63 on 2007-07-11
Hello,

I recently migrated a fileserver from Suse 10.0 to Ubuntu 7.04. The recently installed Ubuntu 7.04 system has 3 add-in disk controllers configured for use with software RAID. The controllers are: Highpoint 1640 4-port (SATA), Highpoint 454 4-port (PATA), and a SIIG SIL-based 4-port (SATA).

Using mdadm I configured 2 matching disks, /dev/sdb and /dev/sdc, as md0 (RAID1) and 2 other matching disks, /dev/sdd and /dev/sde, as md1 (RAID 1), both running off the SIL-based controller. All four disks are the same model. I was able to format and copy data to each RAID disk without any problems encountered. I rebooted several times and the arrays held up fine.

I then halted the system and moved all the SATA cables from the SIL-based card to the Highpoint 1640 and booted the system. The arrays still worked as expected and a cat of /proc/mdstat showed no problems. I moved the cables to see if either controller showed better performance when copying files to the mirrors. Both controllers performed about the same.

Next, I halted the system and installed 2 PATA drives connected to the Highpoint 454 controller. This time, after booting, md0 and md1 showed as only working with 1 out of 2 drives for each array. I assume it has to do with drive enumeration changes caused by the addition of two new drives on the PATA controller which is probably recognized first.

Is this to be expected? Is the configuration of arrays dependent on specific device files or is there some other identifier written to a disk that should allow an array to assemble even if the device file name changes?

Thanks,

Steve

---

