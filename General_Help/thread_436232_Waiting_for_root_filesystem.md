---
title: "Waiting for root filesystem"
date: 2007-05-07
forum: General Help
---

### Post by chadwick359 on 2007-05-07
Just did a fresh install of Feisty on my desk machine at work, and when I'm booting, the machine sits at 'Waiting for the root filesystem.' and sits... and sits some more. Any existing problems with this that I didn't run across in searching? I've attached my boot chart below. Weird thing is, I can't figure out why scsi_eh_1 is even there, as I have no scsi devices.

---

### Post by taurus on 2007-05-07
Feisty sees your /dev/hda as /dev/sda.

Can you boot from the LiveCD and post the output of this command here?

```
sudo fdisk -l
```

---

### Post by chadwick359 on 2007-05-08
Well, that confuses me, and I'm also a bit confused how I missed it.

```
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         622     4996183+  83  Linux
/dev/sda2             623         871     2000092+  82  Linux swap / Solaris
/dev/sda3             872       10011    73417050   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           2       14593   117210240    5  Extended
/dev/sdb5               2       14593   117210208+   7  HPFS/NTFS
```

My fstab file has them labelled as hd instead of sd, which is what they should be.

---

### Post by taurus on 2007-05-08
Let's have a look at your /etc/fstab then.

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
cat /mnt/ubuntu/etc/fstab
```
Post the output of the last command here.

---

### Post by chadwick359 on 2007-05-09
The machine *does* run, but here is my fstab.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=8dc0a110-c260-41f4-b380-e00c54e31ebc /               ext3    defaults,errors=remount-ro ,noatime,data=writeback 0       1
# /dev/hda3
UUID=2c5fd4f6-216e-494a-995a-77e5c9565c92 /home           ext3    defaults        0       2
# /dev/hdb5
UUID=CEF5268932C35F0E /media/UserBkup ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=ffc5cb85-037d-4478-bb89-50d1375e03e2 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by taurus on 2007-05-09
What happens if you replace this line in /etc/fstab

```
UUID=8dc0a110-c260-41f4-b380-e00c54e31ebc /               ext3    defaults,errors=remount-ro ,noatime,data=writeback 0       1
```
with this one.

```
UUID=8dc0a110-c260-41f4-b380-e00c54e31ebc   /    ext3   defaults,errors=remount-ro   0   1
```

---

### Post by feenix9 on 2007-05-14
This may be very very simple, but it was what was causing me problems.  I did not have my hard drive on the primary IDE cable.  I guess that Ubuntu was looking for IDE1 on boot and was not able to find the hard drive.  Just something to think about, I know that we all tend to over look the very simple things.  Thanks to everyone for posting suggestions on here.

---

