---
title: "[SOLVED] Grub / Disk woes"
date: 2007-11-28
forum: General Help
---

### Post by drfox on 2007-11-28
I have a major problem.
I can't boot grub. 

This is the output of sudo fdisk -l

Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x2d38 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24e524e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375        7649    10241437+  83  Linux
/dev/sda3            7650       14593    55777680    5  Extended
/dev/sda5   ?      124016      132638    69252922+  20  Unknown
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8e282988
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8e282988

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sdb2            6375        7649    10241437+  83  Linux
/dev/sdb3            7650       14593    55777680    5  Extended
ubuntu@ubuntu:~$ sudo mkdir /gutsy
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda2 /gutsy
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

When I look at my drives with gparted, all it sees are 2 large, unpartitioned disks

This is my output from the grub prompt:
grub> find /boot/grub/stage1

Error 15: File not found

setup (hd0)

Error 12: Invalid device requested

Finally:
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$ sudo grub-install /dev/hda
/dev/hda: Not found or not a block device.
ubuntu@ubuntu:~$ sudo grub-install /dev/hd0
/dev/hd0: Not found or not a block device.
ubuntu@ubuntu:~$ 

I've tried Super Grub, and that couldn't help, either. Is there anything I can do to rescue my install, or at least my data?

---

### Post by ajgreeny on 2007-11-28
Boot onto the live CD, then add "Disk Mounter" to the panel and see if that can mount your drives.  If so you can at least retrieve your data, if not work out how to boot the system properly.  Seems strange that fdisk finds the partitions but grub doesn't.

---

### Post by drfox on 2007-11-28
> **ajgreeny said:**
> Boot onto the live CD, then add "Disk Mounter" to the panel and see if that can mount your drives.  If so you can at least retrieve your data, if not work out how to boot the system properly.  Seems strange that fdisk finds the partitions but grub doesn't.

Diskmounter is unable to mount either hard drive. Any other suggestions, anyone?

---

### Post by meierfra on 2007-11-28
Try testdisk:  [Hermanzone info on testdisk]("http://www.users.bigpond.net.au/hermanzone/p21.html")

---

### Post by nynoah on 2007-11-28
what came down in the last update.  I have the same problem and there seems to be a rash of Grub Errors.................

---

### Post by drfox on 2007-12-02
> **meierfra said:**
> Try testdisk:  [Hermanzone info on testdisk]("http://www.users.bigpond.net.au/hermanzone/p21.html")

Test disk did it! Thank you very much! I was able to rescue my /home partition from my first drive and a /data partition that I had backed up to my second drive. The rest was trashed, but I don't care. I did a clean install and have all my data back. Thank you! Thank you!

Larry

---

