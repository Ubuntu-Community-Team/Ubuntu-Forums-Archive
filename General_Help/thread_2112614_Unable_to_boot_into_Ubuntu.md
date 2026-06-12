---
title: "Unable to boot into Ubuntu"
date: 2013-02-05
forum: General Help
---

### Post by vicke4 on 2013-02-05
Hi all I had moved partitions along my drive.Now i can't boot into ubuntu.The error i saw was "A error occured while mounting /dev/sda6 press s to skip mounting and m to manual mounting"

where /dev/sda6 is my root directory.My fstab file is as follows:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid                0  0  
# / was on /dev/sda10 during installation
UUID=0770e53c-47df-49bd-b9a4-dc309c160d74  /            ext4  errors=remount-ro                  0  1  
# /home was on /dev/sda11 during installation
UUID=48e299e2-fbcd-47e3-a5c7-f7aa871ea3dd  /home        ext4  defaults                           0  2  
# swap was on /dev/sda8 during installation
UUID=38470f15-f978-4ec8-aa17-cac4d2d80a75  none         swap  defaults                           0  0  
/dev/sda2                                  /media/sda2  ntfs  nls=iso8859-1,umask=000            0  0  
/dev/sda1                                  /media/sda1  ntfs  nls=iso8859-1,ro,noauto,umask=000  0  0  
/dev/sda6                                  /media/sda6  ntfs  nls=iso8859-1,umask=000            0  0  
/dev/sda5                                  /media/sda5  ntfs  defaults                           0  0  
/dev/sda7                                  /media/sda7  ntfs  defaults                           0  0  
/dev/sda9                                  /media/sda9  ntfs  defaults                           0  0  

```

What should i do to make my system bootable?

---

### Post by TheFu on 2013-02-05
I think you need to read the fstab man page.

This line 
```
/dev/sda6                                  /media/sda6  ntfs
```
tells the OS to mount sda6 as NTFS, which is really, really a very bad idea on Linux if that truly is the root partition for the OS.

$ **man fstab**
to gain all understanding required.  Trying to mount non-NTFS formatted disks with NTFS could lead to corruption of the data.

Those UUIDs probably refer to 3 partitions on your drive that you have listed as NTFS below. Bad.  You need to figure out which they are and remove those lines.  Actually, removing all the /media mount attempts until you understand more is probably a good idea.

---

### Post by Impavidus on 2013-02-05
It seems like you repartitioned the drive but left the old fstab in place. As a result, during boot mountall tries to mount /dev/sda6 as ntfs on /media/sda6, which doesn't work because it's an ext4 partition that has to be mounted on / (and probably is mounted there, as the line with the UUID=0770... ,refering to your old sda10, still works).

You'll have to rewrite your /etc/fstab. Use a live cd to boot. There may be some useful tools to help you (I don't know), otherwise  post the output of **sudo fdisk -l** so we get an overview of what's on your drive.

---

### Post by TheFu on 2013-02-05
> **Impavidus said:**
> It seems like you repartitioned the drive but left the old fstab in place. As a result, during boot mountall tries to mount /dev/sda6 as ntfs on /media/sda6, which doesn't work because it's an ext4 partition that has to be mounted on / (and probably is mounted there, as the line with the UUID=0770... ,refering to your old sda10, still works).

You'll have to rewrite your /etc/fstab. Use a live cd to boot. There may be some useful tools to help you (I don't know), otherwise  post the output of **sudo fdisk -l** so we get an overview of what's on your drive.

Doesn't fdisk have issues with GPT disks and HDDs over 2TB?
Safer to use **parted -l**, which works with GPT/MBR, large HDDs and if used for partitioning will automatically align 4K sector HDDs appropriately.

---

### Post by Bucky Ball on 2013-02-05
*Thread moved to **General Help**.*

Maybe the output of:

```
sudo blkid
```

... as well so we can match the UUIDs with the /dev/sda* more clearly as your Linux partitions *were* on 10 and 11.

---

### Post by vicke4 on 2013-02-05
I also involved in this thread this may give you some clue

[http://ubuntuforums.org/showthread.php?t=2111432](http://ubuntuforums.org/showthread.php?t=2111432)

Output of sudo blkid:

```
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="System Reserved" UUID="5C325D54325D346C" TYPE="ntfs" 
/dev/sda2: LABEL="Windows 7" UUID="445C064F5C063C64" TYPE="ntfs" 
/dev/sda5: UUID="38470f15-f978-4ec8-aa17-cac4d2d80a75" TYPE="swap" 
/dev/sda6: UUID="0770e53c-47df-49bd-b9a4-dc309c160d74" TYPE="ext4" 
/dev/sda7: UUID="48e299e2-fbcd-47e3-a5c7-f7aa871ea3dd" TYPE="ext4" 
/dev/sda8: LABEL="CCC" UUID="bdaed6b1-5281-49df-bbf5-666f654652bc" TYPE="ext4" 
/dev/sdb1: LABEL="FreeAgent GoFlex Drive" UUID="9E240D2A240D074D" TYPE="ntfs" 
/dev/sdc1: UUID="DACE-470F" TYPE="vfat" 

```

---

### Post by Bucky Ball on 2013-02-05
You need to go to /etc/fstab and remove the entries for sda5, 6, and 7 as the UUID entries are pointing there already. Use: 

```
sudo nano /etc/fstab
```

... or editor of your choice.

There is a conflict with the /dev/sda* ntfs partition entries as the UUID entries and the /dev/sda* entries are pointing to the same places. The /dev/sda* looks like it's winning but they no longer exist as ntfs. From your blkid, you can see they are now:

```
/dev/sda5: UUID="38470f15-f978-4ec8-aa17-cac4d2d80a75" TYPE="swap" 
/dev/sda6: UUID="0770e53c-47df-49bd-b9a4-dc309c160d74" TYPE="ext4" 
/dev/sda7: UUID="48e299e2-fbcd-47e3-a5c7-f7aa871ea3dd" TYPE="ext4" 
```

I advise you do this:

```
sudo cp /etc/fstab /etc/fstab.backup
```

or something like it before altering fstab. If you screw up, move the original back with:

```
sudo mv /etc/fstab.backup /etc/fstab
```

---

