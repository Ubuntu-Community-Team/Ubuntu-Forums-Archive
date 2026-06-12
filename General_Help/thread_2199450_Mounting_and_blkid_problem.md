---
title: "Mounting and blkid problem"
date: 2014-01-13
forum: General Help
---

### Post by alireza.golabchi on 2014-01-13
hi i have the same problem
when i typed command "sudo blkid" it was requaired a password when i typed than noting isnt typed there pls help me
sorry about grammer im not good att english

---

### Post by Bashing-om on 2014-01-13
alireza.golabchi; Hello ; Welcome to the forum.

Your usage if English is well enough.
We do need to see what the partitioning is on your hard drive(s) and the UUID assignments.
To do this requires the elevated privileges of an administrator (you). One gets these privileges with the use of "sudo" (Super User DO).
The use of "sudo" requires your password, which you blindly enter into the terminal, there is no response to the screen for security reasons,
This is my result for "sudo blkid"
```

sysop@1310mini:~$ sudo blkid
[color=blue][sudo] password for sysop: [/color] ##there will be no response when password is entered##
/dev/sda1: LABEL="1310mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1310mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1204" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1310mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
/dev/sdc1: LABEL="ubie1204" UUID="5bae8c40-b15d-42f8-9fc9-0cf087f338d4" TYPE="ext4" 
sysop@1310mini:~$ 

```
Post back to this forum - between code tags as I did above - the out put of terminal codes:
```

sudo blkid
sudo fdisk -lu

```
And we will continue this discussion of what your problem may be.

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]where there are solutions there are no problems
[/INDENT][/INDENT]

---

### Post by alireza.golabchi on 2014-01-14
i did all the steps and this is the results
```
alireza@alireza-N150P:~$ ls -la /boottotal 30482
drwxr-xr-x  4 root root     1024 Jan 14 03:10 .
drwxr-xr-x 23 root root     4096 Jan 14 03:05 ..
-rw-r--r--  1 root root   853738 Oct  9  2012 abi-3.5.0-17-generic
-rw-r--r--  1 root root   154429 Oct  9  2012 config-3.5.0-17-generic
drwxr-xr-x  5 root root     1024 Jan 14 03:08 grub
-rw-r--r--  1 root root 22208163 Jan 14 03:10 initrd.img-3.5.0-17-generic
drwxr-xr-x  2 root root    12288 Jan 14 02:10 lost+found
-rw-r--r--  1 root root   176764 Oct 11  2012 memtest86+.bin
-rw-r--r--  1 root root   178944 Oct 11  2012 memtest86+_multiboot.bin
-rw-------  1 root root  2320733 Oct  9  2012 System.map-3.5.0-17-generic
-rw-r--r--  1 root root  5171760 Oct 17  2012 vmlinuz-3.5.0-17-generic
alireza@alireza-N150P:~$ ls -la Desktop
total 8
drwxr-xr-x  2 alireza alireza 4096 Jan 14 06:26 .
drwxr-xr-x 25 alireza alireza 4096 Jan 14 06:35 ..
alireza@alireza-N150P:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=416d02c9-0ca9-4b6e-aae2-0e16ac3fc6f2 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu-swap_1 none            swap    sw              0       0
alireza@alireza-N150P:~$ sudo blkid
[sudo] password for alireza: 
/dev/sda1: UUID="416d02c9-0ca9-4b6e-aae2-0e16ac3fc6f2" TYPE="ext2" 
/dev/sda5: UUID="7faca075-8d3d-450c-bd2a-6308e68ab484" TYPE="crypto_LUKS" 
/dev/mapper/sda5_crypt: UUID="3PkZEY-Fb44-9yUy-1XWR-J4tZ-1yLM-CMx312" TYPE="LVM2_member" 
/dev/mapper/ubuntu-root: UUID="f10e2e03-ba60-4dff-bf53-cb4c255e427a" TYPE="ext4" 
/dev/mapper/ubuntu-swap_1: UUID="9477be76-0b11-44e3-9904-189ccbcbebef" TYPE="swap" 
alireza@alireza-N150P:~$ sudo fdisk -lu


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eb469


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   488396799   243947521    5  Extended
/dev/sda5          501760   488396799   243947520   83  Linux


Disk /dev/mapper/sda5_crypt: 249.8 GB, 249800163328 bytes
255 heads, 63 sectors/track, 30369 cylinders, total 487890944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table


Disk /dev/mapper/ubuntu-root: 248.7 GB, 248730615808 bytes
255 heads, 63 sectors/track, 30239 cylinders, total 485801984 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table


Disk /dev/mapper/ubuntu-swap_1: 1065 MB, 1065353216 bytes
255 heads, 63 sectors/track, 129 cylinders, total 2080768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table
alireza@alireza-N150P:~$ mount
/dev/mapper/ubuntu-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
/dev/sda1 on /boot type ext2 (rw)
gvfsd-fuse on /run/user/alireza/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=alireza)



```

---

### Post by papibe on 2014-01-14
Moved to its own thread.

---

### Post by Bucky Ball on 2014-01-14
> **alireza.golabchi said:**
> ... it was requaired a password when i typed than noting isnt typed there ...

There won't be anything there. The password is invisible. Just type it in an hit enter ...

---

### Post by alireza.golabchi on 2014-01-14
i did and the results is up there
please help me i need my files

---

### Post by Bashing-om on 2014-01-14
alireza.golabchi;

From your output of commands it appears you have your files encrypted. That is a layer of protection I know nothing about and is beyond my experience.

Others will have to help who do have that knowledge and experience.

This is one of those things I just do not want to know.

[INDENT][INDENT][INDENT]my best regards
[/INDENT][/INDENT][/INDENT]

---

### Post by alireza.golabchi on 2014-01-14
thanks for your help
i intalled ubuntu again and changed my partitioning and apparently not fixed
i have a question is my secound partition in /home because defined mount point /home
and if this is true how can i see my used storage

---

### Post by Bashing-om on 2014-01-14
alireza.golabchi; Well.

(Re-)install is one sure fire fix,

As to your /home, it can be a separate partition if in the install phase you so designated.
To see your partitions: 
Terminal code:
```

sudo fdisk -lu

```

Depending on how you installed, the used storage - i understand that to be the data that was on the old install - may no longer exist.

More can be advised when the output of "fdisk" is known.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

