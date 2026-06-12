---
title: "LVM -sanity check!"
date: 2018-10-31
forum: General Help
---

### Post by NMeyne on 2018-10-31
Hello All:

In disk manager I have sdc1 - a 120Gb SSD, sdb1 - a 500Gb Hitachi HD and sda - a 3Tb NTFS usb drive
There are also 2 block devices:  496gb dev/ubuntu/root  and   4.3gb dev/ubuntu/swap_1

I get this from lvmdiskscan:

sudo lvmdiskscan -l
  WARNING: only considering LVM devices
  /dev/sdb5          [     465.52 GiB] LVM physical volume
  0 LVM physical volume whole disks
  1 LVM physical volume

I thought is should have been 1 whole disk??   Does this somehow mean I have an UNUSED (old) LVM  / physical volume that I could mount?
..or am I misreading this, and this is correctly mapped to root.

More info...

sudo pvdisplay -m
  --- Physical volume ---
  PV Name               /dev/sdb5
  VG Name               ubuntu
  PV Size               465.52 GiB / not usable 2.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              119173
  Free PE               12
  Allocated PE          119161
  PV UUID               ************************
   
  --- Physical Segments ---
  Physical extent 0 to 118137:
    Logical volume	/dev/ubuntu/root
    Logical extents	0 to 118137
  Physical extent 118138 to 119160:
    Logical volume	/dev/ubuntu/swap_1
    Logical extents	0 to 1022
  Physical extent 119161 to 119172:
    FREE

....

If this all looks OK, I'd like to add another 500Gb HDD to the 'ubuntu' VG, following these instructions:
https://www.digitalocean.com/community/tutorials/how-to-use-lvm-to-manage-storage-devices-on-ubuntu-16-04#create-or-extend-lvm-components


Very grateful for a sanity check from anyone more experienced with this!

Nick

---

### Post by r_widell on 2018-10-31
> **NMeyne said:**
> Hello All:

In disk manager I have sdc1 - a 120Gb SSD, sdb1 - a 500Gb Hitachi HD and sda - a 3Tb NTFS usb drive
There are also 2 block devices:  496gb dev/ubuntu/root  and   4.3gb dev/ubuntu/swap_1

That 500 GB Hitachi HD in its entirety would be sdb.

> **NMeyne said:**
> I get this from lvmdiskscan:

sudo lvmdiskscan -l
  WARNING: only considering LVM devices
  /dev/sdb5          [     465.52 GiB] LVM physical volume
  0 LVM physical volume whole disks
  1 LVM physical volume

I thought is should have been 1 whole disk??   Does this somehow mean I have an UNUSED (old) LVM  / physical volume that I could mount?
..or am I misreading this, and this is correctly mapped to root.

You'll see what else is on that Hitachi drive with ```
sudo fdisk -l /dev/sdb
``` That will show the other partitions and their basic types. SDB5 should show up as a Linux LVM partition, which is where /dev/ubuntu/root and /dev/ubuntu/swap_1 are located.

Note that disk manager is reporting the size as GB, while lvmdiskscan is reporting GiB (one is base 10, the other is base16).

> **NMeyne said:**
> More info...

sudo pvdisplay -m
  --- Physical volume ---
  PV Name               /dev/sdb5
  VG Name               ubuntu
  PV Size               465.52 GiB / not usable 2.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              119173
  Free PE               12
  Allocated PE          119161
  PV UUID               ************************
   
  --- Physical Segments ---
  Physical extent 0 to 118137:
    Logical volume    /dev/ubuntu/root
    Logical extents    0 to 118137
  Physical extent 118138 to 119160:
    Logical volume    /dev/ubuntu/swap_1
    Logical extents    0 to 1022
  Physical extent 119161 to 119172:
    FREE

You have 12 free physical extants of 4.00 MiB each, for a total of 48 MiB. Not much you can do in an LV that small.

> **NMeyne said:**
> ....

If this all looks OK, I'd like to add another 500Gb HDD to the 'ubuntu' VG, following these instructions:
[https://www.digitalocean.com/community/tutorials/how-to-use-lvm-to-manage-storage-devices-on-ubuntu-16-04#create-or-extend-lvm-components](https://www.digitalocean.com/community/tutorials/how-to-use-lvm-to-manage-storage-devices-on-ubuntu-16-04#create-or-extend-lvm-components)


Very grateful for a sanity check from anyone more experienced with this!

Nick

Also note that the man page for lvmdiskscan states ```
This command is deprecated, use pvs instead.
```

Good luck,
ron

---

### Post by NMeyne on 2018-11-03
Thanks very much Ron - much appreciated...  here is the output from fdisk - l /dev/sdb

Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000c13cc

Device     Boot  Start       End            Sectors      Size      Id   Type
/dev/sdb1  *       2048    499711        497664       243M    83  Linux
/dev/sdb2          501758 976771071 976269314 465.5G  5    Extended
/dev/sdb5          501760 976771071 976269312 465.5G  8e   Linux LVM

It looks like from the sector numbers above that sdb5 Linux LVM 'logically' fills/overlaps the entire sdb2 extended partition? 

PVS output is:
 PV               VG          Fmt  Attr   PSize        PFree 
 /dev/sdb5   ubuntu    lvm2  a--  <465.52g    48.00m


If I add another 500mb disk, am I correct in thinking that I should format it as LVM with a default PE size of 4mb again, and then add it to the 'ubuntu' volume group?


Best Regards,

Nick

---

### Post by Dennis N on 2018-11-03
> I'd like to add another 500Gb HDD to the 'ubuntu' VG
First, you need to have a partition on the HDD that's formatted 'LVM2 pv'. You can create and format this partition with gparted.

Then you extend the **ubuntu** volume group to include this partition, using the terminal:

As an example, if the partition you intend to add is **sdb1**,
```
sudo vgextend ubuntu /dev/sdb1
```
Done.

---

### Post by NMeyne on 2018-11-03
Thanks Dennis.   I'll have a go now.   Fingers crossed!
Nick

---

### Post by r_widell on 2018-11-04
> **NMeyne said:**
> Thanks very much Ron - much appreciated...  here is the output from fdisk - l /dev/sdb

Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000c13cc

Device     Boot  Start       End            Sectors      Size      Id   Type
/dev/sdb1  *       2048    499711        497664       243M    83  Linux
/dev/sdb2          501758 976771071 976269314 465.5G  5    Extended
/dev/sdb5          501760 976771071 976269312 465.5G  8e   Linux LVM

It looks like from the sector numbers above that sdb5 Linux LVM 'logically' fills/overlaps the entire sdb2 extended partition? 

Yes, see [HTML]https://en.wikipedia.org/wiki/Master_boot_record[/HTML] for details on the MBR (legacy) disk partitioning (indicated by "Disklabel type: dos" above).
BTW- /dev/sdb1 is your boot partition, likely mounted at /boot.

> **NMeyne said:**
> PVS output is:
 PV               VG          Fmt  Attr   PSize        PFree 
 /dev/sdb5   ubuntu    lvm2  a--  <465.52g    48.00m


If I add another 500mb disk, am I correct in thinking that I should format it as LVM with a default PE size of 4mb again, and then add it to the 'ubuntu' volume group?


Best Regards,

Nick

Yes, and if you want to use the entire drive in your ubuntu VG you won't even need to partition it.
Assuming the new drive will show up as /dev/sdd, you can specify that as the target for your pvcreate command.
N.B.- be sure to confirm the identity of the new drive, ```
ls /dev/disk/by-id
``` will show you all of your drives (/dev/sd?) and all of their partitions. The new drive won't have any partitions.

After adding the new PV to VG ubuntu, you can lvresize(8) any/all of your LVs to expand them (or create a new LV, if you wish). Be sure to use the -r option for lvresize(8) to expand the filesystem to the new space. If you create an new LV you will also need to create a filesystem on it and optionally add it to /etc/fstab to simplify mounting it wherever you choose.

Have fun,
ron

---

