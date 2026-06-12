---
title: "Problem booting using Raid 1 when one drive is missing"
date: 2008-07-09
forum: General Help
---

### Post by Fredrik_b on 2008-07-09
I have followed this guide [http://users.piuha.net/martti/comp/ubuntu/en/install.html](http://users.piuha.net/martti/comp/ubuntu/en/install.html) when installing ubuntu (8.04).

When I remove one of the haddrives I cant boot into ubuntu but end up at the shell mode where it says:
<Initramfs>


What have I done wrong?

---

### Post by fjgaude on 2008-07-09
Did you put **grub** on both drives?

---

### Post by Fredrik_b on 2008-07-09
Something does not look right...

```
Disk /dev/md0: 15.9 GB, 15998058496 bytes
2 heads, 4 sectors/track, 3905776 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/sde: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007225f

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        1945    15623181   fd  Linux raid autodetect
/dev/sde2            1946        2188     1951897+  fd  Linux raid autodetect
/dev/sde3            2189        4864    21494970   fd  Linux raid autodetect

Disk /dev/sdf: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        1945    15623181   fd  Linux raid autodetect
/dev/sdf2            1946        2188     1951897+  fd  Linux raid autodetect
/dev/sdf3            2189        4864    21494970   fd  Linux raid autodetect

Disk /dev/md1: 1998 MB, 1998651392 bytes
2 heads, 4 sectors/track, 487952 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md2: 22.0 GB, 22010724352 bytes
2 heads, 4 sectors/track, 5373712 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

```

No valid partition table?

If I try ti install/reinstall grub I get this error: 

/dev/sdXX does not have any corresponding BIOS drive.

I belive everything wass corect before I removed the harddrive. Do I need to rebuild the Raid array even if nothing was shanged on the drive I temporary removed?

One more thing has changed I have Atached 4 750GB sata disks sins I reatached the harddrive.

---

### Post by fjgaude on 2008-07-09
I'm not sure what is happening. Did you do something like this:

sudo grub
grub> find /boot/grub/stage1

then:

grub> root (hd0,0)
grub> setup (hd0)
grub> quit

then if necessary, out of grub and onto another command line:

sudo grub-install /dev/sda1

---

