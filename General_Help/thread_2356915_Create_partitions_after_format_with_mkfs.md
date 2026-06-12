---
title: "Create partitions after format with mkfs"
date: 2017-03-28
forum: General Help
---

### Post by sed_faster on 2017-03-28
Hello folks,

I use this commando to format my disk:
```

sudo mkfs -c -t ext4 /dev/sdb

```
But now I haven't partitions on my disk. What and how do to create sdb1 partitions, for example?

Thanks

---

### Post by shridhar-kapshikar on 2017-03-28
These commands are EXAMPLES. DELETING partitions, MODIFYING and FORMATTING filesystems destroys data and/or may prevent your machine from booting.  Make backups.  Use at own risk.   Try on a machine you don't mind losing all data on. caveat admin.

To quickly set up a drive up as a single ext4 partition...

    View detected devices of class "DISK"

 ```
   lshw -C disk
```

    View existing partition table(s)

```
    fdisk -l
```

    Edit the partition table for my chosen device (in this case, "sdx")

```
    fdisk /dev/sdx
```

    Within FDISK, press:

        d ...to delete the current partition

        n ...to create a new partition

        p ...to specify it as a PRIMARY partition

        1 ...to set it as the 1ST primary partition

        w ...to write the changes.

    Display the new partition table:

```
    fdisk -l
```

    Format the new partition's filesystem as type ext4

  ```
  mkfs -t ext4 /dev/sdx1
```

    Create a new directory where the new drive will mount into:
```

    mkdir /storage
    mount /dev/sdx1 /storag
```e

---

### Post by sed_faster on 2017-03-28
Thanks,
I prefer mount partition on boot through /etc/fstab. But when I tried do this I receive this message:
```

result sudo blkid /dev/sdc -> /dev/sdc: UUID="dsgsdsdsdfsdfsdfsdf" TYPE="ext4" PTUUID="640e8f4c" PTTYPE="dos"
in /etc/fstab -> UUID=dsgsdsdsdfsdfsdfsdf       /media/folder         ext4    defaults        0       2

sudo mount -a:
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.


```

On another disk if I tried use PARTUUID and I received this error:
```

sudo blkid /dev/sdb1 -> /dev/sdb1: PARTUUID="sdfsdfsdfsdf-01"
sudo mount -a: mount: can't find UUID=f73d95df-01

```

Whats do I wrong?

---

### Post by Dennis N on 2017-03-28
With ext4, you format a partition. **/dev/sdb** designates the disk, not a partition. The first partition on sdb would is designated sdb1.

You need to create a partition table (also called making a disk label), then create one or more partitions, then format the partition(s) using the proper command and device designation:
```
sudo mkfs.ext4 /dev/sda1
```
for creating ext4 file system on first partition of disk sda. All this can be done with gparted, which may be easier.

Additional comment:
But, if you have LVM, a command is the common way to format a logical volume (can't use gparted):
Example:
**sudo mkfs.ext4 /dev/files_vg/data1**
to format logical volume data1 in the files_vg volume group as ext4.

---

### Post by sed_faster on 2017-04-12
The result of the command "sudo fdisk -l" is:

```

Disk /dev/sda: 74.5 GiB, 80026361856 bytes, 156301488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x86c20b0a

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048 152129535 152127488 72.6G 83 Linux
/dev/sda2       152131582 156301311   4169730    2G  5 Extended
/dev/sda5       152131584 156301311   4169728    2G 82 Linux swap / Solaris


Disk /dev/sdb: 153.4 GiB, 164696555520 bytes, 321672960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf73d95df

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1        2048 321672959 321670912 153.4G 83 Linux


Disk /dev/sdc: 74.5 GiB, 80026361856 bytes, 156301488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x640e8f4c

Device     Boot Start       End   Sectors  Size Id Type
/dev/sdc1        2048 156301487 156299440 74.5G 83 Linux


Disk /dev/sdd: 55.9 GiB, 60011642880 bytes, 117210240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x177f177f

Device     Boot Start       End   Sectors  Size Id Type
/dev/sdd1        2048 117209087 117207040 55.9G 83 Linux

```

This is a result of this command:

```

sudo mkfs -c -t ext4 /dev/sdb

```

Is it all good?
Can I use this partition and drive to save my data?

---

### Post by efflandt on 2017-04-14
You put a file system on a partition like **/dev/sdb1**, not the drive /dev/sdb, but maybe mkfs is smart enough to do that properly as a single partition with default msdos partition table on a drive if you leave off the partition number, other than a floppy disk which has no partition table.

I believe blkid has to be hexadecimal. That means 0-9,a-f. So you cannot use letters like "s" or "g". The UUID is usually assigned automatically. For example for the /dev/sdb1 (ext4) that I boot from, the automatically assigned blkid shows: UUID="6787eaaf-0994-4467-897b-538f5c624731"

---

### Post by sed_faster on 2017-04-14
Hello,

Ok, I read this answer: [https://ubuntuforums.org/showthread.php?t=2356915&p=13626186#post13626186](https://ubuntuforums.org/showthread.php?t=2356915&p=13626186#post13626186) and I understand all steps. But If I have a disk with two partitions and want format all disk (I don't know if I should say disk or drive) how and what can I do? I need use fdisk to delete all partitions or exist another tool to format all disk and after this process I should use the steps which you mentioned on previous answer?

---

