---
title: "Salvaging data from a disk with errors - Gparted?"
date: 2015-07-19
forum: General Help
---

### Post by prkos on 2015-07-19
My second computer had an 64GB SSD disk with fedora installed on it. During an automatic update it got stuck, with disk errors (every reboot goes to emergency mode), there may have been power outage that caused this. 

I have tuxboot gparted installed on a USB and it works on my main machine with Ubuntu. 

The idea was to use it on fedora machine and fix the errors, but now I can't even turn it on, maybe power supply went dead. 

So my only option seems to be to load the fedora SSD on my Ubuntu machine and see if I can fix it or retrieve data that way. But when I connected the fedora SSD to my Ubuntu it wouldn't mount. 

Here is the output from some of commands you might need to help (the fedora SSD seems to be on /dev/sdc1): 

```
# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=aa77bec8-6b5f-40d6-8433-461914436514 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=A8C4-48F9  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=fc1b3447-106f-4de2-83a4-950ad9901521 none            swap    sw              0       0

Custom
# /dev/sda4
UUID=e05d7ec2-f0ad-4be9-9a86-1639e6892ccc  /media/username  ext4  defaults  0  2

```

```


# fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  3907029167  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   500118191   250059095+  ee  GPT

Disk /dev/sdc: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005d979

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   125044735    62521344   8e  Linux LVM

Disk /dev/sdd: 4043 MB, 4043309056 bytes
125 heads, 62 sectors/track, 1018 cylinders, total 7897088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00054ddc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          62     7889499     3944719    c  W95 FAT32 (LBA)


```

```

# df
Filesystem      1K-blocks       Used Available Use% Mounted on
/dev/sdb2       229278948   69283680 148325460  32% /
none                    4          0         4   0% /sys/fs/cgroup
udev              8065112         12   8065100   1% /dev
tmpfs             1615184       1120   1614064   1% /run
none                 5120          0      5120   0% /run/lock
none              8075900        436   8075464   1% /run/shm
none               102400         40    102360   1% /run/user
/dev/sdb1          497696       3428    494268   1% /boot/efi
/dev/sda4      1868901088 1146592112 627351284  65% /media/username
/dev/sda2        19091584     883108  17215532   5% /media/username/69586ce6-f654-4b5c-9c3a-3ade74b59bb9
/dev/sda1        19091584   10275044   7823596  57% /media/username/5330b332-b4a6-45fa-8a0f-52d97e1caa36
/dev/sdd1         3937004     176188   3760816   5% /media/username/8FAC-B6FD

```

```
# cat /etc/mtab
/dev/sdb2 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/cgroup tmpfs rw 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0
none /sys/fs/pstore pstore rw 0 0
/dev/sdb1 /boot/efi vfat rw 0 0
/dev/sda4 /media/username ext4 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
systemd /sys/fs/cgroup/systemd cgroup rw,noexec,nosuid,nodev,none,name=systemd 0 0
gvfsd-fuse /run/user/1000/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,user=username 0 0
/dev/sda2 /media/username/69586ce6-f654-4b5c-9c3a-3ade74b59bb9 ext4 rw,nosuid,nodev,uhelper=udisks2 0 0
/dev/sda1 /media/username/5330b332-b4a6-45fa-8a0f-52d97e1caa36 ext4 rw,nosuid,nodev,uhelper=udisks2 0 0
/dev/sdd1 /media/username/8FAC-B6FD vfat rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2 0 0

```

```
# lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
NAME   FSTYPE        SIZE MOUNTPOINT                                          LABEL
sda                  1,8T                                                     
&#9500;&#9472;sda1 ext4         18,6G /media/username/5330b332-b4a6-45fa-8a0f-52d97e1caa36 
&#9500;&#9472;sda2 ext4         18,6G /media/username/69586ce6-f654-4b5c-9c3a-3ade74b59bb9 
&#9500;&#9472;sda3 swap         14,9G                                                     
&#9492;&#9472;sda4 ext4          1,8T /media/username                                      
sdb                238,5G                                                     
&#9500;&#9472;sdb1 vfat          487M /boot/efi                                           
&#9500;&#9472;sdb2 ext4        222,3G /                                                   
&#9492;&#9472;sdb3 swap         15,7G [SWAP]                                              
sdc                 59,6G                                                     
&#9492;&#9472;sdc1 LVM2_member  59,6G                                                     
sdd                  3,8G                                                     
&#9492;&#9472;sdd1 vfat          3,8G /media/username/8FAC-B6FD   
```

```
# mount -t cifs -o ro /dev/sdc1 /media/
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Is there a way I can get to the data on that disk? BTW that disk didn't appear among the options in BIOS to boot from when I connected it to my Ubuntu machine.

---

### Post by NoWayWin8 on 2015-07-19
You could try contacting the device manufacturer, but it's highly unlikely anything on a SSD can be salvaged once the drive has failed.

Then there is this... [http://ubuntuforums.org/showthread.php?t=1245536&p=7822694#post7822694](http://ubuntuforums.org/showthread.php?t=1245536&p=7822694#post7822694) (which says look here: [http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html))

---

### Post by prkos on 2015-07-19
I didn't realize it was that bad! Thank you, I'll try that. 

I found a post from a fedora user who seemed to have gone through a similar situation and he mentioned gparted so I thought it might help here too: 
[https://ask.fedoraproject.org/en/question/40890/every-reboot-fedora-20-goes-to-emergency-mode/#post-id-47556](https://ask.fedoraproject.org/en/question/40890/every-reboot-fedora-20-goes-to-emergency-mode/#post-id-47556)

---

### Post by gedakc on 2015-07-22
Based on the output from the lsblk command, it appears that partition sdc1 contains a Logical Volume Manager Physical Volume.  Typically LVM2 PVs contain LVM2 Logical Volumes which are usually formatted with a file system.  You will need to activate Logical Volume Management first before you can mount the LVM2 LV to access your data.  You might wish to search for an LVM2 tutorial on the web to learn more about Logical Volume Management before trying to recover your data.

---

