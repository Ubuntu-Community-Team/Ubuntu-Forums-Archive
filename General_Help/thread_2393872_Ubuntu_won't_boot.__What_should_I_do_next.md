---
title: "Ubuntu won't boot.  What should I do next?????"
date: 2018-06-09
forum: General Help
---

### Post by dazz100 on 2018-06-09
Hi

I have a dual boot Windows/ Ubuntu desktop.
I have windows and Ubuntu installed on separate SSD.
I have a 3TB HD for data, a 3TB HD for windows applications and a 3TB HD used only for backup of data.
All Ubuntu data is stored on the SSD.

Ubuntu won't boot into the latest version of the Kernel.  It seems to be a problem with sdb2 (The Ubuntu SSD).
It won't boot normally or into recovery.  I suspect that maybe the SSD has failed.  

I can boot into an earlier version of Ubuntu listed on the Grub menu, and I can reach the desktop.

At first I thought it might be a problem with fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=9c4f98f6-a022-4152-beb7-10c52dcb2145 /               ext4    errors=remount-ro 0       1

# /boot/efi was on /dev/nvme0n1p2 during installation
UUID=18AC-B2FA  /boot/efi       vfat    umask=0077      0       1

# /home was on /dev/sda4 during installation
UUID=e6142855-720d-4637-9bb7-f133a15a18c7 /home           ext4    defaults        0       2

# swap was on /dev/sda3 during installation
UUID=65836970-b054-4a03-8567-c794a1a6fb98 none            swap    sw              0       0

proc            /proc           proc    defaults          0       0
#/dev/mmcblk0p1  /boot           vfat    defaults          0       2
#/dev/mmcblk0p2  /               ext4    defaults,noatime  0       1


```

I had a USB stick with a Raspbian installation.  Raspian has ```
/dev/mmcblk0p1 
``` and ```
/dev/mmcblk0p2 
``` partitions but I don't think Ubuntu has these.
I commented these lines out and uncommented the "during installation" lines.

This modified fstab seems to work with the older kernel version but not the latest on the grub menu.

The mount command looks like:
```
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=8097036k,nr_inodes=2024259,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1624848k,mode=755)
**/dev/sdb2 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)**
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=24,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=672)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
configfs on /sys/kernel/config type configfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
**/dev/sdb4 on /home type ext4 (rw,relatime,data=ordered)**
[B]/dev/nvme0n1p2 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
[/B]binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
tmpfs on /run/user/127 type tmpfs (rw,nosuid,nodev,relatime,size=1624844k,mode=700,uid=127,gid=134)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1624844k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sdf1 on /media/darren/USB DISK type vfat (rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)

```

How do I go forward to troubleshoot this problem??

---

### Post by oldfred on 2018-06-09
It shows your UEFI boot on the Windows ESP - efi system partition, the NVMe drive.
Did you create an ESP on the Ubuntu drive, even if not immediately used, I create one on every drive. And have an Ubuntu install on every drive, if only a smaller partition for emergency boot.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 
    
But Boot-Repair uses bootinfoscript for part of report and that has not been updated for NVMe drives nor MMC cards.

---

### Post by dazz100 on 2018-06-09
Hi
I had to Google ESP to find out what it is.  It's been a long time since I did the installation but I would have installed with the default Ubuntu settings.  If that includes an ESP on the Ubuntu drive, it would be there.  

I get an error message that is:
```

VFS: Cannot open root device "sdb2" or unknown-block(0,0): error -6
Pleast append a correct "root=" boot option; here are the available partitions:
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

```

---

### Post by oldfred on 2018-06-09
Your fstab says the drive was sda, but now the errors are from trying to mount partitions on sdb?
UUID should work even if you moved drives around.
But did you add a drive, or change which SATA port it was plugged into.

If you go to the link in my signature and at bottom are Acronyms: and often link to further info.

For all drives post this:
       lsblk -o +PARTUUID /dev/sda
And this:
sudo blkid -c /dev/null -o list

---

### Post by dazz100 on 2018-06-10
Hi
Thanks for the advice.
I haven't changed the drive configuration since installation.
I did accidentally have a bootable Raspian drive in when I booted.
I suspect that drive or grub have updated fstab that is now causing me problems.

I won't be able to provide the outputs you have asked for until next week.

---

### Post by dazz100 on 2018-06-20
Hi
I am writing this using an earlier version of Ubuntu.  It is working perfectly.
 
fstab looks like:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=9c4f98f6-a022-4152-beb7-10c52dcb2145 /               ext4    errors=remount-ro 0       1

# /boot/efi was on /dev/nvme0n1p2 during installation
UUID=18AC-B2FA  /boot/efi       vfat    umask=0077      0       1

# /home was on /dev/sda4 during installation
UUID=e6142855-720d-4637-9bb7-f133a15a18c7 /home           ext4    defaults        0       2

# swap was on /dev/sda3 during installation
UUID=65836970-b054-4a03-8567-c794a1a6fb98 none            swap    sw              0       0

proc            /proc           proc    defaults          0       0
#/dev/mmcblk0p1  /boot           vfat    defaults          0       2
#/dev/mmcblk0p2  /               ext4    defaults,noatime  0       1


```

fdisk -l
```
Disk /dev/nvme0n1: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 1D4985BE-E7F8-49CF-8146-6E5290DB9DE2

Device           Start       End   Sectors   Size Type
/dev/nvme0n1p1    2048    923647    921600   450M Windows recovery environment
/dev/nvme0n1p2  923648   1126399    202752    99M EFI System
/dev/nvme0n1p3 1126400   1159167     32768    16M Microsoft reserved
/dev/nvme0n1p4 1159168 488396799 487237632 232.3G Microsoft basic data


Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x04510450

Device     Boot Start       End   Sectors   Size Id Type
/dev/sda1        2048 488396799 488394752 232.9G  7 HPFS/NTFS/exFAT


Disk /dev/sdb: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 6EFEDAEC-AC43-4C05-B70A-3A981B60A159

Device        Start       End   Sectors   Size Type
/dev/sdb1      2048   1269759   1267712   619M EFI System
/dev/sdb2   1269760  59863039  58593280    28G Linux filesystem
/dev/sdb3  59863040  75487231  15624192   7.5G Linux swap
/dev/sdb4  75487232 488396799 412909568 196.9G Linux filesystem


Disk /dev/sdc: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 7AB33237-84C3-4C76-8859-4E840D64A962

Device     Start        End    Sectors  Size Type
/dev/sdc1   2048 5860532223 5860530176  2.7T Microsoft basic data


Disk /dev/sdd: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: A467EB00-1106-4E95-A16D-D0490A99EEC4

Device      Start        End    Sectors  Size Type
/dev/sdd1      34     262177     262144  128M Microsoft reserved
/dev/sdd2  264192 5860532223 5860268032  2.7T Microsoft basic data



Disk /dev/sde: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: AFE25435-F30E-4CC7-BC19-ADDF10D71D09

Device     Start        End    Sectors  Size Type
/dev/sde1   2048 5860532223 5860530176  2.7T Linux filesystem


```

and the output of mount
```

sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=8097036k,nr_inodes=2024259,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1624848k,mode=755)
/dev/sdb2 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=28,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=500)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
mqueue on /dev/mqueue type mqueue (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/nvme0n1p2 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdb4 on /home type ext4 (rw,relatime,data=ordered)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
tmpfs on /run/user/127 type tmpfs (rw,nosuid,nodev,relatime,size=1624844k,mode=700,uid=127,gid=134)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1624844k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sde1 on /media/darren/Data_bkup type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)

```

I guess this is probably not too much help because it doesn't give information on the boot version of Ubuntu.
I will take a look at the boot tool you posted info on.

---

### Post by dazz100 on 2018-06-20
> **oldfred said:**
> Your fstab says the drive was sda, but now the errors are from trying to mount partitions on sdb?
UUID should work even if you moved drives around.
But did you add a drive, or change which SATA port it was plugged into.

If you go to the link in my signature and at bottom are Acronyms: and often link to further info.

For all drives post this:
       lsblk -o +PARTUUID /dev/sda
And this:
sudo blkid -c /dev/null -o list

The outputs are:
```

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT PARTUUID
sda      8:0    0 232.9G  0 disk            
&#9492;&#9472;sda1   8:1    0 232.9G  0 part            04510450-01
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT PARTUUID
sdb      8:16   0 232.9G  0 disk            
&#9500;&#9472;sdb1   8:17   0   619M  0 part            d9470edc-ef5a-4ac9-9cf7-a1a90a07afed
&#9500;&#9472;sdb2   8:18   0    28G  0 part /          44ef402f-8aa3-44ae-84f2-9d507c25ffe1
&#9500;&#9472;sdb3   8:19   0   7.5G  0 part [SWAP]     2e377171-c05d-4982-b6d3-c341fb73b345
&#9492;&#9472;sdb4   8:20   0 196.9G  0 part /home      4c00ed35-9173-47b7-a538-cb4bacd1cafb
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT PARTUUID
sdc      8:32   0  2.7T  0 disk            
&#9492;&#9472;sdc1   8:33   0  2.7T  0 part            0af00018-fa17-4cbb-83ad-12d024f19b63
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT PARTUUID
sdd      8:48   0  2.7T  0 disk            
&#9500;&#9472;sdd1   8:49   0  128M  0 part            21fe9aed-84ea-4c4d-8b85-29bf2148c372
&#9492;&#9472;sdd2   8:50   0  2.7T  0 part            6d0053e8-310c-4d17-a885-0f25962dee27
device     fs_type label    mount point    UUID

/dev/nvme0n1
                            (in use)       
/dev/nvme0n1p1
           ntfs    Recovery (not mounted)  284AAB434AAB0D1E
/dev/nvme0n1p2
           vfat             /boot/efi      18AC-B2FA
/dev/nvme0n1p3
                            (not mounted)  
/dev/nvme0n1p4
           ntfs             (not mounted)  A47CAECD7CAE9996
/dev/sda1  ntfs    Tmp_Bkup (not mounted)  52C8AAC13FCC2E60
/dev/sdb1  vfat             (not mounted)  8E19-7A3B
/dev/sdb2  ext4             /              9c4f98f6-a022-4152-beb7-10c52dcb2145
/dev/sdb3  swap             [SWAP]         65836970-b054-4a03-8567-c794a1a6fb98
/dev/sdb4  ext4             /home          e6142855-720d-4637-9bb7-f133a15a18c7
/dev/sdc1  ntfs    Win_Apps (not mounted)  61D56FC15A5072E1
/dev/sdd1                   (not mounted)  
/dev/sdd2  ntfs    Data     (not mounted)  C60AAF370AAF2401
/dev/sde1  ext4    Data_bkup /media/darren/Data_bkup 886799f5-d70a-4d62-af99-da2546334ba2

```

---

### Post by oldfred on 2018-06-20
Post #1 shows this:
 UUID=9c4f98f6-a022-4152-beb7-10c52dcb2145 /               ext4    errors=remount-ro 0       1 

But that UUID is not shown in your posts above. Do you have another drive?
UUIDs do not normally change unless you totally reinstalled & reformatted a partition.

---

### Post by dazz100 on 2018-06-21
Hi
I have a HD that is used for backup.  It is working under windows.
I haven't changed any partitions. added disks or anything else.
The only thing I have done is edit fstab.

Below is the output of boot-info.
The link is [http://paste.ubuntu.com/p/gXPgvCzbvH/]("http://paste.ubuntu.com/p/gXPgvCzbvH/")

```

 Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => Windows 2000/XP/2003 is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => Windows 7/8/2012 is installed in the MBR of /dev/sdd.
 => No boot loader is installed in the MBR of /dev/sde.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 17.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  According to the info in the boot sector, sdc1 has 
                       1565562879 sectors, but according to the info from 
                       fdisk, it has 5860530175 sectors.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sdd1: unknown filesystem type ''.

sdd2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  According to the info in the boot sector, sdd2 has 
                       1565300735 sectors, but according to the info from 
                       fdisk, it has 5860268031 sectors.
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   488,396,799   488,394,752   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1   488,397,167   488,397,167  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sdb1                 2,048     1,269,759     1,267,712 EFI System partition
/dev/sdb2             1,269,760    59,863,039    58,593,280 Data partition (Linux)
/dev/sdb3            59,863,040    75,487,231    15,624,192 Swap partition (Linux)
/dev/sdb4            75,487,232   488,396,799   412,909,568 Data partition (Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sdc1                 2,048 5,860,532,223 5,860,530,176 Data partition (Windows/Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

Drive: sdd _____________________________________________________________________
Disk /dev/sdd: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sdd1                    34       262,177       262,144 Microsoft Reserved Partition (Windows)
/dev/sdd2               264,192 5,860,532,223 5,860,268,032 Data partition (Windows/Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

Drive: sde _____________________________________________________________________
Disk /dev/sde: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sde1                 2,048 5,860,532,223 5,860,530,176 Data partition (Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/loop6                                              squashfs   
/dev/nvme0n1                                                       
/dev/nvme0n1p1   284AAB434AAB0D1E                       ntfs       Recovery
/dev/nvme0n1p2   18AC-B2FA                              vfat       
/dev/nvme0n1p3                                                     
/dev/nvme0n1p4   A47CAECD7CAE9996                       ntfs       
/dev/sda1        52C8AAC13FCC2E60                       ntfs       Tmp_Bkup
/dev/sdb1        8E19-7A3B                              vfat       
/dev/sdb2        9c4f98f6-a022-4152-beb7-10c52dcb2145   ext4       
/dev/sdb3        65836970-b054-4a03-8567-c794a1a6fb98   swap       
/dev/sdb4        e6142855-720d-4637-9bb7-f133a15a18c7   ext4       
/dev/sdc1        61D56FC15A5072E1                       ntfs       Win_Apps
/dev/sdd1                                                          
/dev/sdd2        C60AAF370AAF2401                       ntfs       Data
/dev/sde1        886799f5-d70a-4d62-af99-da2546334ba2   ext4       Data_bkup
/dev/sr0         2018-04-26-18-43-51-00                 iso9660    Ubuntu 18.04 LTS amd64

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jun 21 08:53 ata-HL-DT-ST_DVDRAM_GH24NS70_K4NB6TL4921 -> ../../sr0
lrwxrwxrwx 1 root root  9 Jun 21 09:01 ata-ST3000DM008-2DM166_Z504HZV7 -> ../../sdc
lrwxrwxrwx 1 root root 10 Jun 21 09:02 ata-ST3000DM008-2DM166_Z504HZV7-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Jun 21 09:01 ata-ST3000DM008-2DM166_Z504QQGS -> ../../sdd
lrwxrwxrwx 1 root root 10 Jun 21 09:01 ata-ST3000DM008-2DM166_Z504QQGS-part1 -> ../../sdd1
lrwxrwxrwx 1 root root 10 Jun 21 09:02 ata-ST3000DM008-2DM166_Z504QQGS-part2 -> ../../sdd2
lrwxrwxrwx 1 root root  9 Jun 21 09:01 ata-ST3000DM008-2DM166_Z504W41M -> ../../sde
lrwxrwxrwx 1 root root 10 Jun 21 09:01 ata-ST3000DM008-2DM166_Z504W41M-part1 -> ../../sde1
lrwxrwxrwx 1 root root  9 Jun 21 09:01 ata-Samsung_SSD_850_EVO_250GB_S2R4NX0H514531T -> ../../sdb
lrwxrwxrwx 1 root root 10 Jun 21 09:01 ata-Samsung_SSD_850_EVO_250GB_S2R4NX0H514531T-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Jun 21 09:01 ata-Samsung_SSD_850_EVO_250GB_S2R4NX0H514531T-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Jun 21 09:01 ata-Samsung_SSD_850_EVO_250GB_S2R4NX0H514531T-part3 -> ../../sdb3
lrwxrwxrwx 1 root root 10 Jun 21 09:01 ata-Samsung_SSD_850_EVO_250GB_S2R4NX0H514531T-part4 -> ../../sdb4
lrwxrwxrwx 1 root root  9 Jun 21 09:01 ata-WDC_WD2500BEVT-00A1TT0_WD-WX70A69H7145 -> ../../sda
lrwxrwxrwx 1 root root 10 Jun 21 09:02 ata-WDC_WD2500BEVT-00A1TT0_WD-WX70A69H7145-part1 -> ../../sda1
lrwxrwxrwx 1 root root 13 Jun 21 09:01 nvme-Samsung_SSD_960_EVO_250GB_S3ESNX0J555483X -> ../../nvme0n1
lrwxrwxrwx 1 root root 15 Jun 21 09:02 nvme-Samsung_SSD_960_EVO_250GB_S3ESNX0J555483X-part1 -> ../../nvme0n1p1
lrwxrwxrwx 1 root root 15 Jun 21 09:01 nvme-Samsung_SSD_960_EVO_250GB_S3ESNX0J555483X-part2 -> ../../nvme0n1p2
lrwxrwxrwx 1 root root 15 Jun 21 09:01 nvme-Samsung_SSD_960_EVO_250GB_S3ESNX0J555483X-part3 -> ../../nvme0n1p3
lrwxrwxrwx 1 root root 15 Jun 21 09:02 nvme-Samsung_SSD_960_EVO_250GB_S3ESNX0J555483X-part4 -> ../../nvme0n1p4
lrwxrwxrwx 1 root root 13 Jun 21 09:01 nvme-eui.0025385571b27616 -> ../../nvme0n1
lrwxrwxrwx 1 root root 15 Jun 21 09:02 nvme-eui.0025385571b27616-part1 -> ../../nvme0n1p1
lrwxrwxrwx 1 root root 15 Jun 21 09:01 nvme-eui.0025385571b27616-part2 -> ../../nvme0n1p2
lrwxrwxrwx 1 root root 15 Jun 21 09:01 nvme-eui.0025385571b27616-part3 -> ../../nvme0n1p3
lrwxrwxrwx 1 root root 15 Jun 21 09:02 nvme-eui.0025385571b27616-part4 -> ../../nvme0n1p4
lrwxrwxrwx 1 root root  9 Jun 21 08:53 usb-Generic-_Compact_Flash_058F63626479-0:0 -> ../../sdf
lrwxrwxrwx 1 root root  9 Jun 21 08:53 usb-Generic-_MS_MS-PRO_058F63626479-0:2 -> ../../sdh
lrwxrwxrwx 1 root root  9 Jun 21 08:53 usb-Generic-_SD_MMC_058F63626479-0:1 -> ../../sdg
lrwxrwxrwx 1 root root  9 Jun 21 08:53 usb-Generic-_xD-Picture_058F63626479-0:3 -> ../../sdi
lrwxrwxrwx 1 root root  9 Jun 21 09:01 wwn-0x5000c500a2760a20 -> ../../sdc
lrwxrwxrwx 1 root root 10 Jun 21 09:02 wwn-0x5000c500a2760a20-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Jun 21 09:01 wwn-0x5000c500a2e9a253 -> ../../sdd
lrwxrwxrwx 1 root root 10 Jun 21 09:01 wwn-0x5000c500a2e9a253-part1 -> ../../sdd1
lrwxrwxrwx 1 root root 10 Jun 21 09:02 wwn-0x5000c500a2e9a253-part2 -> ../../sdd2
lrwxrwxrwx 1 root root  9 Jun 21 09:01 wwn-0x5000c500a395ef41 -> ../../sde
lrwxrwxrwx 1 root root 10 Jun 21 09:01 wwn-0x5000c500a395ef41-part1 -> ../../sde1
lrwxrwxrwx 1 root root  9 Jun 21 09:01 wwn-0x50014ee2adacfc03 -> ../../sda
lrwxrwxrwx 1 root root 10 Jun 21 09:02 wwn-0x50014ee2adacfc03-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 Jun 21 09:01 wwn-0x5002538d40e4d717 -> ../../sdb
lrwxrwxrwx 1 root root 10 Jun 21 09:01 wwn-0x5002538d40e4d717-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Jun 21 09:01 wwn-0x5002538d40e4d717-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Jun 21 09:01 wwn-0x5002538d40e4d717-part3 -> ../../sdb3
lrwxrwxrwx 1 root root 10 Jun 21 09:01 wwn-0x5002538d40e4d717-part4 -> ../../sdb4

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime,nojoliet,check=s,map=n,blocksize=2048)


=========================== sdb2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="2"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
set root='hd1,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  9c4f98f6-a022-4152-beb7-10c52dcb2145
else
  search --no-floppy --fs-uuid --set=root 9c4f98f6-a022-4152-beb7-10c52dcb2145
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_NZ
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=30
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=30
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-9c4f98f6-a022-4152-beb7-10c52dcb2145' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_gpt
	insmod ext2
	set root='hd1,gpt2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  9c4f98f6-a022-4152-beb7-10c52dcb2145
	else
	  search --no-floppy --fs-uuid --set=root 9c4f98f6-a022-4152-beb7-10c52dcb2145
	fi
        linux	/boot/vmlinuz-4.13.0-39-generic root=/dev/sdb2 ro  quiet splash $vt_handoff
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-9c4f98f6-a022-4152-beb7-10c52dcb2145' {
	menuentry 'Ubuntu, with Linux 4.13.0-39-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.13.0-39-generic-advanced-9c4f98f6-a022-4152-beb7-10c52dcb2145' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  9c4f98f6-a022-4152-beb7-10c52dcb2145
		else
		  search --no-floppy --fs-uuid --set=root 9c4f98f6-a022-4152-beb7-10c52dcb2145
		fi
		echo	'Loading Linux 4.13.0-39-generic ...'
	        linux	/boot/vmlinuz-4.13.0-39-generic root=/dev/sdb2 ro  quiet splash $vt_handoff
	}
	menuentry 'Ubuntu, with Linux 4.13.0-39-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.13.0-39-generic-init-upstart-9c4f98f6-a022-4152-beb7-10c52dcb2145' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  9c4f98f6-a022-4152-beb7-10c52dcb2145
		else
		  search --no-floppy --fs-uuid --set=root 9c4f98f6-a022-4152-beb7-10c52dcb2145
		fi
		echo	'Loading Linux 4.13.0-39-generic ...'
	        linux	/boot/vmlinuz-4.13.0-39-generic root=/dev/sdb2 ro  quiet splash $vt_handoff init=/sbin/upstart
	}
	menuentry 'Ubuntu, with Linux 4.13.0-39-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.13.0-39-generic-recovery-9c4f98f6-a022-4152-beb7-10c52dcb2145' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  9c4f98f6-a022-4152-beb7-10c52dcb2145
		else
		  search --no-floppy --fs-uuid --set=root 9c4f98f6-a022-4152-beb7-10c52dcb2145
		fi
		echo	'Loading Linux 4.13.0-39-generic ...'
	        linux	/boot/vmlinuz-4.13.0-39-generic root=/dev/sdb2 ro recovery nomodeset 
	}
	menuentry 'Ubuntu, with Linux 4.13.0-38-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.13.0-38-generic-advanced-9c4f98f6-a022-4152-beb7-10c52dcb2145' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  9c4f98f6-a022-4152-beb7-10c52dcb2145
		else
		  search --no-floppy --fs-uuid --set=root 9c4f98f6-a022-4152-beb7-10c52dcb2145
		fi
		echo	'Loading Linux 4.13.0-38-generic ...'
		linux	/boot/vmlinuz-4.13.0-38-generic.efi.signed root=UUID=9c4f98f6-a022-4152-beb7-10c52dcb2145 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.13.0-38-generic
	}
	menuentry 'Ubuntu, with Linux 4.13.0-38-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.13.0-38-generic-init-upstart-9c4f98f6-a022-4152-beb7-10c52dcb2145' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  9c4f98f6-a022-4152-beb7-10c52dcb2145
		else
		  search --no-floppy --fs-uuid --set=root 9c4f98f6-a022-4152-beb7-10c52dcb2145
		fi
		echo	'Loading Linux 4.13.0-38-generic ...'
		linux	/boot/vmlinuz-4.13.0-38-generic.efi.signed root=UUID=9c4f98f6-a022-4152-beb7-10c52dcb2145 ro  quiet splash $vt_handoff init=/sbin/upstart
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.13.0-38-generic
	}
	menuentry 'Ubuntu, with Linux 4.13.0-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.13.0-38-generic-recovery-9c4f98f6-a022-4152-beb7-10c52dcb2145' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  9c4f98f6-a022-4152-beb7-10c52dcb2145
		else
		  search --no-floppy --fs-uuid --set=root 9c4f98f6-a022-4152-beb7-10c52dcb2145
		fi
		echo	'Loading Linux 4.13.0-38-generic ...'
		linux	/boot/vmlinuz-4.13.0-38-generic.efi.signed root=UUID=9c4f98f6-a022-4152-beb7-10c52dcb2145 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.13.0-38-generic
	}
	menuentry 'Ubuntu, with Linux 4.13.0-37-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.13.0-37-generic-advanced-9c4f98f6-a022-4152-beb7-10c52dcb2145' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  9c4f98f6-a022-4152-beb7-10c52dcb2145
		else
		  search --no-floppy --fs-uuid --set=root 9c4f98f6-a022-4152-beb7-10c52dcb2145
		fi
		echo	'Loading Linux 4.13.0-37-generic ...'
		linux	/boot/vmlinuz-4.13.0-37-generic.efi.signed root=UUID=9c4f98f6-a022-4152-beb7-10c52dcb2145 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.13.0-37-generic
	}
	menuentry 'Ubuntu, with Linux 4.13.0-37-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.13.0-37-generic-init-upstart-9c4f98f6-a022-4152-beb7-10c52dcb2145' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  9c4f98f6-a022-4152-beb7-10c52dcb2145
		else
		  search --no-floppy --fs-uuid --set=root 9c4f98f6-a022-4152-beb7-10c52dcb2145
		fi
		echo	'Loading Linux 4.13.0-37-generic ...'
		linux	/boot/vmlinuz-4.13.0-37-generic.efi.signed root=UUID=9c4f98f6-a022-4152-beb7-10c52dcb2145 ro  quiet splash $vt_handoff init=/sbin/upstart
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.13.0-37-generic
	}
	menuentry 'Ubuntu, with Linux 4.13.0-37-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.13.0-37-generic-recovery-9c4f98f6-a022-4152-beb7-10c52dcb2145' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  9c4f98f6-a022-4152-beb7-10c52dcb2145
		else
		  search --no-floppy --fs-uuid --set=root 9c4f98f6-a022-4152-beb7-10c52dcb2145
		fi
		echo	'Loading Linux 4.13.0-37-generic ...'
		linux	/boot/vmlinuz-4.13.0-37-generic.efi.signed root=UUID=9c4f98f6-a022-4152-beb7-10c52dcb2145 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.13.0-37-generic
	}
	menuentry 'Ubuntu, with Linux 4.13.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.13.0-36-generic-advanced-9c4f98f6-a022-4152-beb7-10c52dcb2145' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  9c4f98f6-a022-4152-beb7-10c52dcb2145
		else
		  search --no-floppy --fs-uuid --set=root 9c4f98f6-a022-4152-beb7-10c52dcb2145
		fi
		echo	'Loading Linux 4.13.0-36-generic ...'
		linux	/boot/vmlinuz-4.13.0-36-generic.efi.signed root=UUID=9c4f98f6-a022-4152-beb7-10c52dcb2145 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.13.0-36-generic
	}
	menuentry 'Ubuntu, with Linux 4.13.0-36-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.13.0-36-generic-init-upstart-9c4f98f6-a022-4152-beb7-10c52dcb2145' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  9c4f98f6-a022-4152-beb7-10c52dcb2145
		else
		  search --no-floppy --fs-uuid --set=root 9c4f98f6-a022-4152-beb7-10c52dcb2145
		fi
		echo	'Loading Linux 4.13.0-36-generic ...'
		linux	/boot/vmlinuz-4.13.0-36-generic.efi.signed root=UUID=9c4f98f6-a022-4152-beb7-10c52dcb2145 ro  quiet splash $vt_handoff init=/sbin/upstart
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.13.0-36-generic
	}
	menuentry 'Ubuntu, with Linux 4.13.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.13.0-36-generic-recovery-9c4f98f6-a022-4152-beb7-10c52dcb2145' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  9c4f98f6-a022-4152-beb7-10c52dcb2145
		else
		  search --no-floppy --fs-uuid --set=root 9c4f98f6-a022-4152-beb7-10c52dcb2145
		fi
		echo	'Loading Linux 4.13.0-36-generic ...'
		linux	/boot/vmlinuz-4.13.0-36-generic.efi.signed root=UUID=9c4f98f6-a022-4152-beb7-10c52dcb2145 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.13.0-36-generic
	}
	menuentry 'Ubuntu, with Linux 4.10.0-42-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.10.0-42-generic-advanced-9c4f98f6-a022-4152-beb7-10c52dcb2145' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  9c4f98f6-a022-4152-beb7-10c52dcb2145
		else
		  search --no-floppy --fs-uuid --set=root 9c4f98f6-a022-4152-beb7-10c52dcb2145
		fi
		echo	'Loading Linux 4.10.0-42-generic ...'
		linux	/boot/vmlinuz-4.10.0-42-generic.efi.signed root=UUID=9c4f98f6-a022-4152-beb7-10c52dcb2145 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.10.0-42-generic
	}
	menuentry 'Ubuntu, with Linux 4.10.0-42-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.10.0-42-generic-init-upstart-9c4f98f6-a022-4152-beb7-10c52dcb2145' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  9c4f98f6-a022-4152-beb7-10c52dcb2145
		else
		  search --no-floppy --fs-uuid --set=root 9c4f98f6-a022-4152-beb7-10c52dcb2145
		fi
		echo	'Loading Linux 4.10.0-42-generic ...'
		linux	/boot/vmlinuz-4.10.0-42-generic.efi.signed root=UUID=9c4f98f6-a022-4152-beb7-10c52dcb2145 ro  quiet splash $vt_handoff init=/sbin/upstart
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.10.0-42-generic
	}
	menuentry 'Ubuntu, with Linux 4.10.0-42-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.10.0-42-generic-recovery-9c4f98f6-a022-4152-beb7-10c52dcb2145' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  9c4f98f6-a022-4152-beb7-10c52dcb2145
		else
		  search --no-floppy --fs-uuid --set=root 9c4f98f6-a022-4152-beb7-10c52dcb2145
		fi
		echo	'Loading Linux 4.10.0-42-generic ...'
		linux	/boot/vmlinuz-4.10.0-42-generic.efi.signed root=UUID=9c4f98f6-a022-4152-beb7-10c52dcb2145 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.10.0-42-generic
	}
	menuentry 'Ubuntu, with Linux 4.10.0-40-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.10.0-40-generic-advanced-9c4f98f6-a022-4152-beb7-10c52dcb2145' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  9c4f98f6-a022-4152-beb7-10c52dcb2145
		else
		  search --no-floppy --fs-uuid --set=root 9c4f98f6-a022-4152-beb7-10c52dcb2145
		fi
		echo	'Loading Linux 4.10.0-40-generic ...'
		linux	/boot/vmlinuz-4.10.0-40-generic.efi.signed root=UUID=9c4f98f6-a022-4152-beb7-10c52dcb2145 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.10.0-40-generic
	}
	menuentry 'Ubuntu, with Linux 4.10.0-40-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.10.0-40-generic-init-upstart-9c4f98f6-a022-4152-beb7-10c52dcb2145' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  9c4f98f6-a022-4152-beb7-10c52dcb2145
		else
		  search --no-floppy --fs-uuid --set=root 9c4f98f6-a022-4152-beb7-10c52dcb2145
		fi
		echo	'Loading Linux 4.10.0-40-generic ...'
		linux	/boot/vmlinuz-4.10.0-40-generic.efi.signed root=UUID=9c4f98f6-a022-4152-beb7-10c52dcb2145 ro  quiet splash $vt_handoff init=/sbin/upstart
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.10.0-40-generic
	}
	menuentry 'Ubuntu, with Linux 4.10.0-40-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.10.0-40-generic-recovery-9c4f98f6-a022-4152-beb7-10c52dcb2145' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  9c4f98f6-a022-4152-beb7-10c52dcb2145
		else
		  search --no-floppy --fs-uuid --set=root 9c4f98f6-a022-4152-beb7-10c52dcb2145
		fi
		echo	'Loading Linux 4.10.0-40-generic ...'
		linux	/boot/vmlinuz-4.10.0-40-generic.efi.signed root=UUID=9c4f98f6-a022-4152-beb7-10c52dcb2145 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.10.0-40-generic
	}
}

### END /etc/grub.d/10_linux ###





=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of sdb2, using the following options:        sdb1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot use-standard-efi-file


=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sdb1/efi/.../grub*.efi file!

If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\...\grub*.efi


=================== User settings
The settings chosen by the user will not act on the boot.





```

---

### Post by oldfred on 2018-06-21
Sorry, mixed up UUID and PartUUID. The PARTUUID is the GUID with gpt partitioned drives.
So this is correct.
UUID=9c4f98f6-a022-4152-beb7-10c52dcb2145 /               ext4    errors=remount-ro 0       1 

The first part of the Boot-Repair summary report is bootinfoscript.
I filed a request to have bootinfoscript include more info on NVMe drives, but he needs someone to test it as neither of us has NVMe drive.
       Support NVMe and MMC devices 
[https://github.com/arvidjaar/bootinfoscript/issues](https://github.com/arvidjaar/bootinfoscript/issues)

If you go into Disks (Gnome Disks) and in upper right corner icon is Smart Status. Does it show your drive as good/passed. All I know is good or bad, but it can run many detailed tests and report those details.

---

### Post by dazz100 on 2018-06-22
Hi
OK so I have used Disks to check the disk status including SMART.  The disks all show the disks are healthy.  All the SMART data shows OK.
The 2nd most recent version of Ubuntu boots and runs fine.  The latest version just dies.  I just get a blank screen.  If I can delete or overwrite the mangled version things might go back to normal.

I have a backup of all my home data.  I don't have a backup of the applications and file system.

---

### Post by oldfred on 2018-06-22
I have high speed Internet, and my backup is just adpkg list of installed apps, so I can reinstall them, if I have to do a new install. 
And I backup my data, not system.

---

### Post by dazz100 on 2018-06-30
Hi
Given that I have an earlier version running OK, wondering if I could try upgrading from there and hopefully repair/overwrite the broken version???

---

### Post by dazz100 on 2018-07-03
Hi
I fixed this problem by starting from a previous version of the OS, which worked perfectly, and upgrading from there.  I am now running the latest version of Ubuntu and all is good.

---

