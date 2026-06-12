---
title: "Need Help With Devil External Hard Drive!!"
date: 2006-12-23
forum: General Help
---

### Post by nzk on 2006-12-23
So I have an ext3 formatted external usb hard drive. Ubuntu doesn't see it besides in nautilus, which is of no help because clicking on it makes a mount error.

I can't mount because if i try it says that "no such device"

here is my fstab (the drive is the 2nd /dev/sda1, since i cant get it to be the first :|)
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=24211a22-07f4-475c-a941-81ef48832238 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=0081e46c-a40c-4d69-a217-d934993b5333 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1   /media/share   ext3   defaults   0   2
/dev/sda1 /media/wherever ext3 defaults,user,other-options 0 0

```

---

### Post by taurus on 2006-12-23
This one doesn't even look right!!!

```
/dev/sda1 /media/wherever ext3 defaults,user,other-options 0 0
```
You need to modify your /etc/fstab

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and replace the line above with this new line.

```
/dev/sda1   /media/sda1   ext3   defaults   0   1
```
Save it.  Then create a mount point and mount it...

```
sudo mkdir /media/sda1
sudo mount -a
df -h
```

---

### Post by nzk on 2006-12-23
```
andrei@andrei-laptop:~$ sudo mkdir /media/sda1
andrei@andrei-laptop:~$ sudo mount -a
mount: special device /dev/sda1 does not exist
mount: mount point /media/wherever does not exist

```

---

### Post by taurus on 2006-12-23
You already have /dev/sda1 mounted in /etc/fstab!

```
/dev/sda1   /media/share   ext3   defaults   0   2
```
What's the output of this command from a terminal and your /etc/fstab again?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by nzk on 2006-12-23
sudo fdisk -l
```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6996    56195338+  83  Linux
/dev/hda2            6997        7296     2409750    5  Extended
/dev/hda5            6997        7296     2409718+  82  Linux swap / Solaris

```

cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=24211a22-07f4-475c-a941-81ef48832238 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=0081e46c-a40c-4d69-a217-d934993b5333 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1   /media/sda1   ext3   defaults   0   1
/dev/sda1 /media/wherever ext3 defaults,user,other-options 0 0

```

---

### Post by taurus on 2006-12-23
Did you plug in your USB drive because it didn't show up on "sudo fdisk -l"???  Also, you _need_ to remove the last line in your /etc/fstab because it doesn't even make any sense and besides, you already have an entry for /dev/sda1 (just above it)...

```
/dev/sda1 /media/wherever ext3 defaults,user,other-options 0 0
```

---

### Post by nzk on 2006-12-23
HMM!

Doing fstab -l like mad yielded:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=24211a22-07f4-475c-a941-81ef48832238 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=0081e46c-a40c-4d69-a217-d934993b5333 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1   /media/sda1   ext3   defaults   0   1

```

---

### Post by taurus on 2006-12-23
> **nzk said:**
> HMM!

Doing fstab -l like mad yielded:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=24211a22-07f4-475c-a941-81ef48832238 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=0081e46c-a40c-4d69-a217-d934993b5333 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1   /media/sda1   ext3   defaults   0   1

```

Your /etc/fstab looks fine now.  However, do you have that external USB connected to your computer!  If you have, it should show up with

```
sudo fdisk -l
```

---

### Post by nzk on 2006-12-23
it doesnt show up.

---

### Post by taurus on 2006-12-23
It's on and plugged in!!!

---

### Post by nzk on 2006-12-23
it sees it now 
```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6996    56195338+  83  Linux
/dev/hda2            6997        7296     2409750    5  Extended
/dev/hda5            6997        7296     2409718+  82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321    7  HPFS/NTFS

```

---

### Post by taurus on 2006-12-23
Wait!  /dev/sda1 is NOT ext3!  It's ntfs...  Therefore, this line in /etc/fstab is wrong...

```
/dev/sda1   /media/sda1   ext3   defaults   0   1
```
It should be

```
/dev/sda1   /media/sda1   ntfs   nls=utf8,umask=0222  0  0
```

---

### Post by nzk on 2006-12-23
how do i format it to ext3?

---

### Post by taurus on 2006-12-23
Do you currently have it mount?  Make sure you don't have it mount first before you format it.  This command will tell you whether it's mounted or not.

```
df -h
```
And if you want to format /dev/sda1 to ext3, then run

```
sudo mke2fs -j /dev/sda1
```
Please make sure you've backed up everything in /dev/sda1 first or it's gone...

---

### Post by nzk on 2006-12-23
it shows up in df -h, how do i unmount it?!

---

### Post by taurus on 2006-12-23
```
sudo umount /dev/sda1
df -h
```

---

### Post by nzk on 2006-12-23
Argh. Getting ubuntu to see it is like rolling a die. I have to turn it on and off 20 times quickly, the do fdisk -l until it shows

---

### Post by nzk on 2006-12-23
and after a few minutes, it doesnt show anymore

---

### Post by nzk on 2006-12-23
doing that reformatting command does:
```
mke2fs 1.39 (29-May-2006)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
19546112 inodes, 39072080 blocks
1953604 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=41943040
1193 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424, 20480000, 23887872

Writing inode tables: done                            
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir

```

and doing fdisk -l again says its still ntfs...

---

### Post by taurus on 2006-12-23
Looks to me like your external USB drive is a little iffy!!!  Do you have a machine running XP?  Maybe you want to connect to a XP machine and defrag your USB drive first?

---

### Post by nzk on 2006-12-24
let me try

---

### Post by nzk on 2006-12-24
windows said it was unformatted, now it is ntfs. let me try that command again

---

### Post by nzk on 2006-12-24
same stupid error "ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir
"

---

### Post by taurus on 2006-12-24
See if you can format it to ext3 using gparted!

---

### Post by nzk on 2006-12-24
gparted errors when trying to format /dev/sda1 to ext3

---

### Post by nzk on 2006-12-24
any ideas now?

---

### Post by nzk on 2006-12-24
bump

---

### Post by nzk on 2006-12-26
Bump! Hello Is Anyone Here!

---

