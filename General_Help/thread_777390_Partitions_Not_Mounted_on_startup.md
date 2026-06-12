---
title: "Partitions Not Mounted on startup"
date: 2008-05-01
forum: General Help
---

### Post by soumen08 on 2008-05-01
Hello,
Just shifted to hardy and facing strange problems.. I have multiple partitions and in hardy they aren't mounted on startup unlike gutsy where they used to be there on startup. can someone suggest a suitable method to automate the process especially at startup?
thanks,
Soumen

---

### Post by joshsmith on 2008-05-01
partitions that are mounted at boot are listed in /etc/fstab
run in terminal, and post the output of 
cat /etc/fstab
which outputs the text of that file

or try and work out the necessary other lines from the lines you already have there. ie mine looks like this. (always back up first)

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=e3cb81c8-e93c-4fd3-8185-6fb2894d48ce /               ext3    errors=remount-ro 0       1
# /dev/hda1
UUID=1EC9C311301E26FA /media/hda1     ntfs    defaults,umask=000,gid=46 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

as a piece of more general advice, if you ever want to automate anything, work out the terminal command, then put them in a text file, make the text file executable, and add it to you system startup in system>preferences>sessions. 
this isnt the ideal solution here, as to mount things you need to type in your adminstrator password, (so the script would still would but you would be prompted for a password). therefore its best to get the entries into /etc/fstab to do when it is supposed to happen

---

### Post by soumen08 on 2008-05-02
The Output is
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=103b8ecf-c754-4e30-89d0-f422a237abe0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=4da52955-a4cc-4316-996b-325a4456de70 none            swap    sw              0       0
# /dev/sda9
UUID=5f5694cb-151b-4133-911f-bf2123aac921 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I want to mount /dev/sda5 and /dev/sda1
but i dont know the UUID of those. How do i find them?
Thanks,
Soumen

---

### Post by danwood76 on 2008-05-02
You dont need the UUIDs, the block device is fine.
Only use UUIDs if your drives swap block device numbers a lot.

Can you give us the output of fdisk -l

```

sudo fdisk -l

```
this will enable us to create you a couple of new fstab lines

---

### Post by duckville on 2008-05-02
danwood76 is right, you don't need to know the uuid, but...

ls -l /dev/disk/by-uuid/

that command should give you all the uuid that the corresponding partition e.g. /dev/sda1 on the drive.

note:
if you were to make changes to the partition e.g. delete & re-create... then the uuid would change. 

good luck

---

### Post by soumen08 on 2008-05-02
This was the output of the by uuid command I thought that since all lines seem to be commented except for the ones with uuids i'll need the uuid. well make me the lines!
Thank You

lrwxrwxrwx 1 root root 10 2008-05-02 18:36 103b8ecf-c754-4e30-89d0-f422a237abe0 -> ../../sda6
lrwxrwxrwx 1 root root 10 2008-05-02 18:36 5f5694cb-151b-4133-911f-bf2123aac921 -> ../../sda7
lrwxrwxrwx 1 root root 10 2008-05-02 18:36 644469244468F9E6 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-05-02 18:36 70297873-4e0d-45b1-bd3c-6c86ec9df5b1 -> ../../sda8
lrwxrwxrwx 1 root root  9 2008-05-02 15:34 A61C-3F1F -> ../../sdb
lrwxrwxrwx 1 root root 10 2008-05-02 18:36 BA08AA9008AA4AE9 -> ../../sda1

---

### Post by danwood76 on 2008-05-02
still need to know the partition information aswell.
We need to know filesystems and so on.

Its easier if you do an fdisk list.
```

sudo fdisk -l

```

---

### Post by soumen08 on 2008-05-02
Output of the fdisk command

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x56cc390a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3191    25631676    7  HPFS/NTFS
/dev/sda2            3192        9729    52516485    f  W95 Ext'd (LBA)
/dev/sda5            3192        7119    31551628+   7  HPFS/NTFS
/dev/sda6            7963        9607    13213431   83  Linux
/dev/sda7            9608        9729      979933+  82  Linux swap / Solaris
/dev/sda8            7120        7962     6771366   83  Linux

Partition table entries are not in disk order

---

### Post by soumen08 on 2008-05-02
Output of the fdisk command

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x56cc390a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3191    25631676    7  HPFS/NTFS
/dev/sda2            3192        9729    52516485    f  W95 Ext'd (LBA)
/dev/sda5            3192        7119    31551628+   7  HPFS/NTFS
/dev/sda6            7963        9607    13213431   83  Linux
/dev/sda7            9608        9729      979933+  82  Linux swap / Solaris
/dev/sda8            7120        7962     6771366   83  Linux

Partition table entries are not in disk order

---

### Post by danwood76 on 2008-05-04
OK so we want 2 new fstab lines to accomodate the 2 NTFS partitions.

so the new lines will be:
```

# /dev/sda1
UUID=BA08AA9008AA4AE9 /media/HD1 ntfs-3g defaults 0 0
# /dev/sda5
UUID=644469244468F9E6 /media/HD2 ntfs-3g defaults 0 0

```
open up the fstab for editiing:
```

sudo gedit /etc/fstab

```
then paste the above lines at the end of the file and save.

then we need to create the mount points:
```

sudo mkdir /media/HD1
sudo mkdir /media/HD2

```
right now if you reboot it should mount the 2 partitions to /media/HD1 and /media/HD2.

---

