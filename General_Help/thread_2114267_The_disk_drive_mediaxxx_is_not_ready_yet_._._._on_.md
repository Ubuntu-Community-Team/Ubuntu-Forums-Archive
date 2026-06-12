---
title: "The disk drive /media/xxx is not ready yet . . . on boot up"
date: 2013-02-09
forum: General Help
---

### Post by ineuw on 2013-02-09
This issue was posted and discussed back in 2011 and can be found under the following links but is till not resolved. (Also, some links in the above posts no longer work).

[http://askubuntu.com/questions/34997/disk-drive-not-ready-yet-or-not-available#comment315204_35467](http://askubuntu.com/questions/34997/disk-drive-not-ready-yet-or-not-available#comment315204_35467)

[http://ubuntuforums.org/showthread.php?t=1724209](http://ubuntuforums.org/showthread.php?t=1724209)

After using Boot-repair to recover my multi-boot desktop, everything is fine except at boot I get the following message: **"The disk drive /media/xxx is not ready yet or not present".** After pressing S for skip, Xubuntu boots up fine and the drive in question is mounted as read & write.

On reboot, I tried the remedies listed in the above posts through the terminal option of the message.

Again, everything works fine, everything is updated to the latest releases, but I would like to get rid of the interruption during boot. Responses are most appreciated.

---

### Post by dabl on 2013-02-09
I'd like to see the output of these terminal commands:

```
sudo blkid -c /dev/null -o list
```

```
sudo fdisk -lu
```

```
cat /etc/fstab
```

---

### Post by ineuw on 2013-02-09
> **dabl said:**
> I'd like to see the output of these terminal commands:
```
sudo blkid -c /dev/null -o list

sudo fdisk -lu

cat /etc/fstab
```

dabl, thanks for your quick reply. Here are the three outputs

ineuw@SANFRANCISCO:~$ sudo blkid -c /dev/null -o list
[sudo] password for ineuw: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    Joe     (not mounted)  BC5C1D795C1D2F9E
/dev/sda3  swap             <swap>         6adfa227-71a3-45a3-b848-23a818ad6676
/dev/sda5  ntfs    Natalie     /media/Natalie    79BCA47A0352E8AF
/dev/sda6  ext4    Eli   /              b9114ddb-61e3-4eb7-95e1-cbd712066f73
/dev/sdb1  ntfs    Adele     /media/Adele    68801CB8801C8F26
/dev/sdb3  ntfs    Alvin   /media/Alvin  3ACC1816CC17CB51
/dev/sdb5  ntfs    Dina    /media/Dina   EC94959A9495683A



ineuw@SANFRANCISCO:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0bba0bb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    51199154    25599546    7  HPFS/NTFS/exFAT
/dev/sda2        51200059   151328767    50064354+   5  Extended
/dev/sda3       151328768   156301311     2486272   82  Linux swap / Solaris
/dev/sda5        51200061   104454629    26627284+   7  HPFS/NTFS/exFAT
/dev/sda6       104456192   151328767    23436288   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe44d8d0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    51199154    25599546    7  HPFS/NTFS/exFAT
/dev/sdb2        51199155   102398309    25599577+   f  W95 Ext'd (LBA)
/dev/sdb3   *   102398310   156296384    26949037+   7  HPFS/NTFS/exFAT
/dev/sdb5        51199218   102398309    25599546    7  HPFS/NTFS/exFAT



ineuw@SANFRANCISCO:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc           proc     nodev,noexec,nosuid                                                   0  0  
#Entry for /dev/sda6 :
UUID=b9114ddb-61e3-4eb7-95e1-cbd712066f73  /               ext4     errors=remount-ro                                                     0  1  
#Entry for /dev/sdb1 :
UUID=68801CB8801C8F26                      /media/Adele     ntfs-3g  defaults                                                              0  0  
#Entry for /dev/sdb3 :
UUID=3ACC1816CC17CB51                      /media/Alvin   ntfs-3g  defaults                                                              0  0  
#Entry for /dev/sdb5 :
UUID=EC94959A9495683A                      /media/Dina    ntfs-3g  defaults                                                              0  0  
#Entry for /dev/sda1 :
UUID=7E14FE0514FDC067                      /media/Joe     ntfs-3g  defaults                                                              0  0  
#Entry for /dev/sda5 :
UUID=79BCA47A0352E8AF                      /media/Natalie     ntfs-3g  defaults                                                              0  0  
#Entry for /dev/sda4 :
UUID=6adfa227-71a3-45a3-b848-23a818ad6676  none            swap     sw                                                                    0  0  
/dev/fd0                                   /media/floppy0  auto     rw,user,noauto,exec,utf8                                              0  0  

END

---

### Post by dabl on 2013-02-09
You've got a wrong UUID in /etc/fstab for /dev/sda1. So when you boot, /etc/fstab is coughing up an error, and your "S" skips it, allowing the system to boot without mounting /dev/sda1.

The correct UUID for /dev/sda1 is ```
BC5C1D795C1D2F9E
```, as shown by blkid.  Open /etc/fstab in a root-mode text editor, copy and paste the correct UUID into the /dev/sda1 mount line, and then save it, and run

```
sudo mount -a
```

Then confirm it's mounted with 

```
sudo mount
```

If you see that it is now mounted, I think your system will be fixed.

---

### Post by ineuw on 2013-02-09
dabl, many thanks. Everything is as it should be.

---

### Post by dcstar on 2013-02-09
> **dabl said:**
> You've got a wrong UUID in /etc/fstab for /dev/sda1. ........

And the fact that there should be **no** /media entries in /etc/fstab doesn't help.

**/media is a System Folder for exclusive use of the System** to mount and unmount removable devices and if a user want to mount these things, then they must use another mount point (like /mnt).

---

