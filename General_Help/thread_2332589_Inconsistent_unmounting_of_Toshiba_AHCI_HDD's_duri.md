---
title: "Inconsistent unmounting of Toshiba AHCI HDD's during shutdown"
date: 2016-08-01
forum: General Help
---

### Post by bcschmerker on 2016-08-01
I currently have Ubuntu® 16.04.1-LTS installed across four SATA drives in AHCI mode (one Western Digital® WD1600JS-55NCB1, /dev/sda; three Toshiba® MQ01ABD050's, /deb/sdb, /dev/sdc and /dev/sdd) and one EIDE drive (Seagate® ST380215A, /dev/sde).  I noticed that my system has hit-and-miss unmounting of partitions on the Toshibas, going down for either reboot or halt (whereas the WD and Seagate are consistent in unmounts); when a "failed unmounting" occurs, it automatically starts /sbin/fsck.btr and/or /sbin/fsck.ext4 as required on the next boot.  What factors may be involved in the Toshibas' inconsistencies in AHCI mode?

---

System Board:  Gigabyte® GA-MA78GM-S2HP Rev. 2.0 (AMD RS780G northbridge/SB710 southbridge)
MPU:  2.80 GHz Advanced Micro Devices® Athlon64® X2 5600+ (200MHz base clock x14)
Main Memory: 4 GiB DDR2-667

---

### Post by gordintoronto on 2016-08-02
It's not clear what you mean by "across four SATA drives." You don't mean LVM or RAID, do you?

Is it correct that you have a mix of btrfs and ext4?

---

### Post by bcschmerker on 2016-08-02
This is in fact not a RAID or LVM; each of the SATA drives carries unique partitions specific to mount points.  The WD1600JS (/dev/sda) carries ext4 partitions for /boot and filesystem root; the first MQ01ABD050 (/dev/sdb), ext4 partitions for /usr, /opt, and /srv; the second MQ01ABD050 (/dev/sdc), a BTrFS partition for /var; the third MQ01ABD050 (/dev/sdd), a BTrFS partition for /home.  All four of the above have extended subpartitions of 8 GiB capacity per each for swap.  The first clue I noticed during original installation was a possible misbehavior of the partitioning tool on each of the MQ01ABD050's, as it reported displacement of the primary partition from Cylinder 0 on each drive by an identical number of KiB; this did not occur on the WD1600JS.

---

### Post by gordintoronto on 2016-08-03
All you need is one swap partition. You might try deleting the extraneous ones. I doubt if that is the source of your problem, though.

I can't imagine what it would take to fill the first and third drives to 10% of their capacity.

---

