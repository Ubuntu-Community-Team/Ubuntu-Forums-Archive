---
title: "Mdadm Raid1 missing 1 drive."
date: 2018-08-07
forum: General Help
---

### Post by frackingawesome on 2018-08-07
I have a client that created a raid1 array out of 2 external USB drives.  Then one of those drives crashed (the click of death).  i have and can view the remaining drive in doth fdisk as well as mdadm -misc  Those results are below. the device is at /dev/sdb with 4 partitions 1-4.  I believe sdb4 is the partition i am looking for. mdadm says it is raid 1 with only 1 drive missing.  But when i try to assemble it i get mdadm: device /dev/sdb4 exists but is not an md array.  What am i doing wrong?  



**fdisk Results**
*Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors**Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*
*Disklabel type: dos*
*Disk identifier: 0x00007c00*

*Device     Boot   Start        End    Sectors   Size Id Type*
*/dev/sdb1         48195    5927984    5879790   2.8G fd Linux raid autodetect*
*/dev/sdb2       5927985    6136829     208845   102M fd Linux raid autodetect*
*/dev/sdb3       6136830    8112824    1975995 964.9M fd Linux raid autodetect*
*/dev/sdb4       8112825 1953520064 1945407240 927.7G fd Linux raid autodetect*


*Disk /dev/md127: 964.8 MiB, 1011613696 bytes, 1975808 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/md126: 2.8 GiB, 3010330624 bytes, 5879552 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/md125: 101.9 MiB, 106823680 bytes, 208640 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/md124: 927.7 GiB, 996048437248 bytes, 1945407104 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*

[B]lsblk -f results
[/B]*NAME      FSTYPE            LABEL UUID                                 MOUNTPOINT*
*sda                                                                    *
*&#9500;&#9472;sda1    ext4                    58cb750f-9189-4d46-abec-3ca85115cadd /*
*&#9500;&#9472;sda2                                                                 *
*&#9492;&#9472;sda5    swap                    3274c4aa-8891-4205-8433-3d67d56ccc59 [SWAP]*
*sdb                                                                    *
*&#9500;&#9472;sdb1    linux_raid_member       5c4faa37-b5bf-edea-c272-7f5d63a39bc8 *
*&#9474; &#9492;&#9472;md124 ext3                    68923fef-80a1-467a-ab1d-8054f38bd517 *
*&#9500;&#9472;sdb2    linux_raid_member       2423f78a-8e6c-ff10-a9a8-cac9f3dbe460 *
*&#9474; &#9492;&#9472;md127 swap                                                         *
*&#9500;&#9472;sdb3    linux_raid_member       4a29369d-fdda-1410-ea26-ae92cde60e79 *
*&#9474; &#9492;&#9472;md126 ext3                    1b3a4c59-8983-4579-ac36-6b1010c7b50a *
*&#9492;&#9472;sdb4    linux_raid_member       6392b004-2852-fb20-7dc9-0d5bf5adf4b3 *
*  &#9492;&#9472;md125 ext3                    958e1f7b-63cb-4553-b30b-787ab8886720 *
*sr0                                                                    *
*sr1                                                                    *
[B]mdadm --misc /dev/sdb4 results
[/B]*/dev/sdb4:*
*          Magic : a92b4efc*
*        Version : 0.90.00*
*           UUID : 6392b004:2852fb20:7dc90d5b:f5adf4b3*
*  Creation Time : Mon Nov 12 09:05:15 2007*
*     Raid Level : raid1*
*  Used Dev Size : 972703552 (927.64 GiB 996.05 GB)*
*     Array Size : 972703552 (927.64 GiB 996.05 GB)*
*   Raid Devices : 2*
*  Total Devices : 1*
*Preferred Minor : 4*

*    Update Time : Wed Dec 31 19:00:08 1969*
*          State : clean*
* Active Devices : 1*
*Working Devices : 1*
* Failed Devices : 1*
*  Spare Devices : 0*
*       Checksum : 29cfaa69 - correct*
*         Events : 689248*


*      Number   Major   Minor   RaidDevice State*
*this     0       8        4        0      active sync*

*   0     0       8        4        0      active sync*
*   1     1       0        0        1      faulty removed*

---

