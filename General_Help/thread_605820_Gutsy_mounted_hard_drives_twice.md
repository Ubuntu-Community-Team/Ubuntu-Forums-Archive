---
title: "Gutsy mounted hard drives twice??"
date: 2007-11-07
forum: General Help
---

### Post by mattgaunt on 2007-11-07
Hey everyone

I just updated to gutsy gibbon on my desktop

After mounting all my partitions to /mnt/ rather than media i rebooted and it has now mounted my USB pen drive and external hard drive twice.

Any ideas why that might be?

Ill restart and see if it helps

Gaunt

---

### Post by ohzopants on 2007-11-07
When you say you mounted them to /mnt/ do you mean you changed fstab file, or did you do it manually?  Are they mounted twice in the same place?

That does sound pretty weird...

---

### Post by taurus on 2007-11-07
Post

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by rubicon on 2007-11-07
I have such problem too. It is happen randomly when I leave usb-drive connected at reboot. It is still mounted as /media/USBSTICK, and then, somehow, my Ubuntu Gutsy manages to mount it again, this time in /media/USBSTICK_ (note the underscore).

Not a big problem though, all I got to do is to unmount all of its instances and re-insert usb-drive to my pc. Or manually mount again.

---

### Post by mattgaunt on 2007-11-07
I found just restarting it fixed the problem, i changed the internal hard drives to under /mnt/ in the fstab file

Gaunt

---

### Post by syxbit on 2007-12-27
i'm getting this problem too
did a clean install of gutsy x64. on some bootups my external USB HD shows up twice, on others, just once. weird

sudo fdisk -l
```
Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2b3500cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27461   220572672    7  HPFS/NTFS
/dev/sda2           27462       30413    23711940   83  Linux
/dev/sda3           30414       90836   485347747+  83  Linux
/dev/sda4           90837       91201     2931862+  82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009ed8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       91201   732572001   83  Linux

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b93bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1       60801   488384001   83  Linux

```

cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=e8e5fe37-55bc-47d3-90a2-bdf161c6edfd /               ext3    defaults,errors=remount-ro 0       0
# /dev/sda3
UUID=5465e869-547c-464b-9e0c-094f5ce3c713 /home           ext3    defaults        0       0
# /dev/sdb1
UUID=0841f1a4-aba2-4d07-91a3-a1e254841319 /media/WD2      ext3    defaults        0       0
# /dev/sda1
UUID=5C1E5AFA1E5ACD20 /media/windows  ntfs    defaults,umask=007,gid=46 0       0
# /dev/sda4
UUID=15600880-374e-46a4-9a73-3dd35ef5e351 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


```

df -h

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              23G  3.0G   19G  15% /
varrun                2.0G   96K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  156K  2.0G   1% /dev
devshm                2.0G     0  2.0G   0% /dev/shm
lrm                   2.0G   14M  2.0G   1% /lib/modules/2.6.22-14-generic/volatile
/dev/sda3             456G  1.2G  432G   1% /home
/dev/sdb1             688G  398G  255G  61% /media/WD2
/dev/sda1             211G   89G  123G  42% /media/windows
/dev/sdg1             459G  363G   73G  84% /media/WD ext.

```

any ideas?

---

