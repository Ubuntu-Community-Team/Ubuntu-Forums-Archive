---
title: "HP Hardware Raid Array A - Logical Drives - Logical Drive 1 - Creates 2 Drives"
date: 2023-03-15
forum: General Help
---

### Post by qombi on 2023-03-15
I just created a hardware raid on a HP proliant server and when I log in to Ubuntu 22.04 and run the command below I see two drives listed. One drive is expected, the logical drive created from multiple hard drives. However there is another drive listed sdb, that shows 0 for the size that is new as well. I was hoping maybe someone could explain to me why I see this drive. Thanks 

lsblk
NAME                      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0                       7:0    0  63.3M  1 loop /snap/core20/1822
loop1                       7:1    0  63.3M  1 loop /snap/core20/1828
loop2                       7:2    0 111.9M  1 loop /snap/lxd/24322
loop3                       7:3    0  49.8M  1 loop /snap/snapd/18357
sda                         8:0    0  87.3T  0 disk
**sdb                         8:16   1     0B  0 disk**

---

### Post by MAFoElffen on 2023-03-15
Please post the results of these within CODE Tags:
```

lsblk -o name,size,type,fstype,mountpoints | grep -v 'loop\|snap'
sudo fdisk -l 2>&1 | sed '/\/dev\/loop/,+3 d' 2> /dev/null | uniq

```

---

### Post by qombi on 2023-03-16
lsblk -o name,size,type,fstype,mountpoints | grep -v 'loop\|snap'
NAME                        SIZE TYPE FSTYPE      MOUNTPOINTS
sda                        87.3T disk LVM2_member
&#9492;&#9472;data_vg-data_lv            87T lvm  xfs         /data_fs
sdb                           0B disk
nvme0n1                   447.1G disk
&#9500;&#9472;nvme0n1p1                   1G part vfat        /boot/efi
&#9500;&#9472;nvme0n1p2                   2G part ext4        /boot
&#9492;&#9472;nvme0n1p3                 444G part LVM2_member
  &#9492;&#9472;ubuntu--vg-ubuntu--lv   400G lvm  ext4        /


fdisk -l 2>&1 | sed '/\/dev\/loop/,+3 d' 2> /dev/null | uniq

Disk /dev/nvme0n1: 447.07 GiB, 480036519936 bytes, 937571328 sectors
Disk model: HPE NS204i-p Gen10+ Boot Controller
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 55210DE3-582D-4BA6-9BA1-117314894293

Device           Start       End   Sectors  Size Type
/dev/nvme0n1p1    2048   2203647   2201600    1G EFI System
/dev/nvme0n1p2 2203648   6397951   4194304    2G Linux filesystem
/dev/nvme0n1p3 6397952 937568255 931170304  444G Linux filesystem

Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 400 GiB, 429496729600 bytes, 838860800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/sda: 87.31 TiB, 96000840564736 bytes, 187501641728 sectors
Disk model: LOGICAL VOLUME
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 262144 bytes / 2097152 bytes

Disk /dev/mapper/data_vg-data_lv: 87 TiB, 95657511616512 bytes, 186831077376 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 262144 bytes / 2097152 bytes


Does this help?

---

### Post by MAFoElffen on 2023-03-16
/dev/sda is your RAID drive 1? And it is hard RAID right?

Just in lsblk, I see /dev/sdb 0 bytes... But it doesn't show up with fdisk.

What does this show?
```

grep . /proc/diskstats
grep . /proc/mdstat
grep 'sdb' /proc/mounts

```
Sidenote: Please try to wrap your output in CODE Tags.

Example:
[noparse]```

Paste Output here

```[/noparse]

---

### Post by svinky-99 on 2023-03-21
> **qombi said:**
> I just created a hardware raid on a HP proliant server and when I log in to Ubuntu 22.04 and run the command below I see two drives listed. One drive is expected, the logical drive created from multiple hard drives. However there is another drive listed sdb, that shows 0 for the size that is new as well. I was hoping maybe someone could explain to me why I see this drive. Thanks 

lsblk
NAME                      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0                       7:0    0  63.3M  1 loop /snap/core20/1822
loop1                       7:1    0  63.3M  1 loop /snap/core20/1828
loop2                       7:2    0 111.9M  1 loop /snap/lxd/24322
loop3                       7:3    0  49.8M  1 loop /snap/snapd/18357
sda                         8:0    0  87.3T  0 disk
**sdb                         8:16   1     0B  0 disk**


Based on the output of the lsblk command that you shared, it seems that the second drive sdb is recognized as a disk with a size of 0 bytes. This behavior could be due to various reasons, such as a hardware issue, a problem with the RAID configuration, or a driver compatibility issue.


One possibility is that the HP hardware RAID controller is creating a RAID 1 configuration, which mirrors the data across two disks for redundancy. In this case, the logical drive you created is split across two physical disks, and the sdb device represents the mirror disk that is used for redundancy.


Another possibility is that the disk is not properly detected by the operating system due to driver issues or incompatibilities. You could try checking the system logs or running other disk management utilities to get more information about the issue.


Overall, it's recommended to consult the documentation of the RAID controller and the operating system to identify the root cause of the issue and ensure that the RAID configuration is set up correctly. You may find [this page]("https://hpe.to/660637xwy") helpful as well.

---

### Post by MAFoElffen on 2023-03-21
I would suggest that you run the [UbuntuForums 'system-info' Script]("https://github.com/UbuntuForums/system-info") and post the URL of the where the script uploads the report to a pastebin...

I was thinking when I wrote my first post, that maybe you should post a phone picture of your SMART Array config so we can see what is there.

That report includes an extensive storage section that will identify what storage devices are being used with their respective drivers. Better to see the information there, than to guess or assume. 

Without that. I am thinking that is something in the HP SMART Array Controller configuration. One thing I didn't like about working with my my HP servers was having to use their HP Smart Array boot disk, just to configure my arrays. Dell PE servers, it's easy to just be able to config them, on the fly, by using their PERC RAID Controller BIOS and toggling into them during boot, via the hot-keys.

---

