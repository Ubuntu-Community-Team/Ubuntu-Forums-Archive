---
title: "GRUB install no working?"
date: 2014-03-15
forum: General Help
---

### Post by AlliumPorrum on 2014-03-15
I tried to restore my Ubuntu setup backed up with fsarchiver. I formatted the destination USB disk, restored from the archive, and then tried to install the brub to the destination to make it bootable. But, it does not work:

[I]:~$ sudo grub-install --root-directory=/mnt /dev/sdb
/usr/sbin/grub-bios-setup: warning: Attempting to install GRUB to a disk with multiple partition labels.  This is not supported yet..
/usr/sbin/grub-bios-setup: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..[/I]

What's wrong with this??

---

### Post by grahammechanical on 2014-03-15
Where do you want to install Grub to? is it sdb? Are you running the live session or another installation of Ubuntu? Mount the hard disk. and run

```
sudo grub-install /dev/sdb
```

That works for me.

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

Regards.

---

### Post by AlliumPorrum on 2014-03-16
With that command, I get exactly the same error message. Why why why oh why??

---

### Post by Bashing-om on 2014-03-16
AlliumPorrum; Hi !


Here is my little bit to start to try and help.

Back to square 1, with the "destination USB disk" connected, 
Post the output - between code tags - of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Once the device is identified and a mount point created, the install command will execute ( make sure that BOTH working from version and the install to versions are the same !).

[INDENT]ain't nothing but a thing
[/INDENT]

---

### Post by oldfred on 2014-03-16
In addition to bashing-on suggestions, was sdb a gpt drive and you converted to MBR or vice-versa?

Grub will not install correctly to a gpt partition drive unless you also have a bios_grub partition. Or if Linux sees it is both MBR & gpt it gets confused.

---

### Post by AlliumPorrum on 2014-03-19
> **Bashing-om said:**
> AlliumPorrum; Hi !

Here is my little bit to start to try and help.

Back to square 1, with the "destination USB disk" connected, 
Post the output - between code tags - of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Once the device is identified and a mount point created, the install command will execute ( make sure that BOTH working from version and the install to versions are the same !).

[INDENT]ain't nothing but a thing
[/INDENT]

Here you go:

:~$ sudo fdisk -lu

Disk /dev/sda: 8011 MB, 8011120640 bytes
247 heads, 62 sectors/track, 1021 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00027dc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    13672447     6835200   83  Linux
/dev/sda2        13674494    15429631      877569    5  Extended
/dev/sda5        13674496    15429631      877568   82  Linux swap / Solaris

Disk /dev/sdb: 7798 MB, 7798947840 bytes
22 heads, 33 sectors/track, 20981 cylinders, total 15232320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001dd5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    15230975     7614464   83  Linux


~$ sudo parted -l
Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sda: 8011MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  7000MB  6999MB  primary   ext4            boot
 2      7001MB  7900MB  899MB   extended
 5      7001MB  7900MB  899MB   logical   linux-swap(v1)


Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdb: 7799MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  7798MB  7797MB  primary  ext4


:~$ sudo grub-install /dev/sdb
/usr/sbin/grub-bios-setup: warning: Attempting to install GRUB to a disk with multiple partition labels.  This is not supported yet..
/usr/sbin/grub-bios-setup: error: embedding is not possible, but this is required for cross-disk install.

---

