---
title: "Unable to mount /dev/sda5"
date: 2007-10-13
forum: General Help
---

### Post by EmyrB on 2007-10-13
Hi all

I have a slight problem mounting a partition that is on a SATA drive. The output of 
```
fdisk -l /dev/sda
``` brings up this: -

```
Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x971ff0ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       39164   314576797+   f  W95 Ext'd (LBA)
/dev/sda2           39165       48641    76124002+   7  HPFS/NTFS
/dev/sda5               2       13055   104856223+   7  HPFS/NTFS
/dev/sda6           13056       26109   104856223+   7  HPFS/NTFS
/dev/sda7           26110       39164   104864256    7  HPFS/NTFS


```

and when I try and issue
```
mount /dev/sda5
```
or
```
ntfs-3g /dev/sda5 /media/sda5
```
or
```
mount /media/sda5
```
ends with the same error: -
```
fuse: failed to access mountpoint /media/sda5: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sda5 (VM's)

```

Should I try and mount sda first, then sda5?

Any help would be very gratefully received.

Cheers

EmyrB

---

### Post by nikhilk on 2007-10-13
Does your fstab have an entry for /dev/sda5?

---

### Post by EmyrB on 2007-10-13
I did put it in there, but '#'ed it out when it wouldn't mount. Here is my fstab: -

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=5ef785f0-9c52-4df3-868b-8c536e038c83 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb3
UUID=dbfeb803-5175-4b53-ba96-6a5c526031ae /home           ext3    defaults        0       2
# /dev/hda2
UUID=30D41A44D41A0D2A /media/hda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda5
UUID=48D02CB1D02CA762 /media/hda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda6
UUID=6EC0323DC0320BB9 /media/hda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
# UUID=5C5C2E7C5C2E50D6 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdb4
UUID=a378ba6f-ae6a-467e-841b-c6330c855b33 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

---

### Post by nikhilk on 2007-10-13
You mean you still get the same error after uncommenting the /media/sda5 line in fstab and running mount -a? How about removing the UUID stuff and instead directly putting in /dev/sda5?

---

### Post by EmyrB on 2007-10-13
Did that, rebooted and still no icon on the desktop. So I issued ```
sudo mount -a
``` and I get the following error: -

```

fuse: failed to access mountpoint /media/sda5: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sda5 (VM's)

```

Now that I have uncommented it, it does not show up under Places > Computer, where as if I commented it out it does, but it won't mount. The other partitions on sda do mount. I know the partition is good as if I boot in to XP I can read and write to the partition.

---

### Post by nikhilk on 2007-10-13
EmyrB, I do not mean to sound condescending, but seeing the error message "fuse: failed to access mountpoint /media/sda5: No such file or directory" have you confirmed that /media/sda5 exists?
I checked my fstab entry for a ntfs partion I mount using ntfs-3g and it seems pretty similar to yours (except for an extra nls=utf8 option). Did this problem arise recently. I mean did the sda5 used to mount correctly previously?

---

### Post by EmyrB on 2007-10-13
sda5 works fine under windows XP but all I am trying to do is have access to it under Linux. /media/sda5 doesn't exist in the media directory, but neither did hda6 until I issued a mount command, so why should this be any different. Maybe I should try and mount other partitions on the same SATA

---

### Post by PmDematagoda on 2007-10-13
Can you see the drive/partition in Gnome partition editor?

---

### Post by vanadium on 2007-10-13
You *have* to create the mount point manually when mounting partitions of fixed disks using fstab. Thus, create a directory /media/sda5, then issue "mount -a" and most likely all will work right.

[edit]Studying your fdisk into more detail, I see that you are already mounting partition 5 under /media/hda5. With the /dev/sda5 line, you are just trying to mount the same partition again (yes, what once was hda5 on your system is now sda5!). Yet, in both cases, a different UUID is displayed.

Leave the sda5 lines commented out and continue to work on the hda5 line. It is likely that one is mounted already. Check with the command "mount". If not, you will need to check the UUID of sda5 and put the correct UUID in place of the current one.

---

### Post by chiragjog on 2007-10-19
Hi,
I upgraded from Feisty to Gutsy.
After upgrading i see that my NTFS partition is not mounted(which previously was).

SO i try a manual mount and get this error.
-----------------------------------------------
sudo mount /dev/sda1 /media/
mount: according to mtab, /dev/sda1 is already mounted on /media

FUSE mount point creation failed
Unmounting /dev/sda1 ()
------------------------------------------------

Here is my /etc/mtab

------------------------------------------------
chirag@hells-kitchen:~$ cat /etc/mtab
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw 0 0
/dev/disk/by-uuid/88da9686-a89d-4618-bc78-19be9390fefd / ext3 rw,data=ordered 0 0
/dev/disk/by-uuid/88da9686-a89d-4618-bc78-19be9390fefd /dev/.static/dev ext3 rw,data=ordered 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
/dev/sda7 /media/sda7 vfat rw,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec 0 0
--------------------------------------------------------------------
which doesnt have sda1 

Is this related to above issue ?

---

