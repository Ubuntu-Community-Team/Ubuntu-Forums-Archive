---
title: "GRUB gives error 18 when booting system (after 1 week of use in ubuntu)"
date: 2008-06-23
forum: General Help
---

### Post by dinbrca on 2008-06-23
ok i tried to boot my computer (restarted it because of ubuntu updates and more) and then (i have dual boot) GRUB loads shows:
GRUB Loading..
GRUB Stage1.5:
Error 18

I saw it happens to a lot of people.. i searched for it in some resources sites and came up that it might be something with the HD
and i thought that reinstalling GRUB might help... so.. i got into the live CD of ubuntu and then opened a terminal and entered:
sudo grub
it went ok and then i tried to enter
find /boot/grub/stage1 and click enter but it doesnt let me =/
thx for the helpers..
BTW:
maybe i am new to linux (only started to know it before one week) but i found it intersting (i think its a challange but i find a lot of bugs in hardy heron =/) so i dont want to use windows xp for now..

---

### Post by dinbrca on 2008-06-23
someone please?

---

### Post by VMC on 2008-06-23
"Error 18: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time."

Do this from a Terminal:

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

Then we can find a solution.

---

### Post by dinbrca on 2008-06-24
sudo fdisk -l
gives:
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04d304d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         443     3558366    7  HPFS/NTFS
/dev/sda2             444       38912   309002242+   f  W95 Ext'd (LBA)
/dev/sda5            9139       35246   209712478+   7  HPFS/NTFS
/dev/sda6           35247       38912    29447113+   7  HPFS/NTFS
/dev/sda7             444        8778    66950824+  83  Linux
/dev/sda8            8779        9138     2891668+  82  Linux swap / Solaris

Partition table entries are not in disk order

```
cat /boot/grub/menu.lst
gives:
```

cat: /boot/grub/menu.lst: No such file or directory

```

---

### Post by VMC on 2008-06-24
> **dinbrca said:**
> sudo fdisk -l
gives:
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04d304d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         443     3558366    7  HPFS/NTFS
/dev/sda2             444       38912   309002242+   f  W95 Ext'd (LBA)
/dev/sda5            9139       35246   209712478+   7  HPFS/NTFS
/dev/sda6           35247       38912    29447113+   7  HPFS/NTFS
/dev/sda7             444        8778    66950824+  83  Linux
/dev/sda8            8779        9138     2891668+  82  Linux swap / Solaris

Partition table entries are not in disk order

```
cat /boot/grub/menu.lst
gives:
```

cat: /boot/grub/menu.lst: No such file or directory

```
From the LiveCd type:
```
sudo mkdir /mnt/tmp
sudo mount /dev/sda7 /mnt/tmp
cat /mnt/tmp/boot/grub/menu.lst
```

---

### Post by meierfra. on 2008-06-24
The OP has solved the Error 18 problem by reinstalling and now is fighting with  different problems:

[http://ubuntuforums.org/showthread.php?t=839569]("http://ubuntuforums.org/showthread.php?t=839569")

---

