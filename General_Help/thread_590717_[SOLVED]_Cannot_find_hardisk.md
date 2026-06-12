---
title: "[SOLVED] Cannot find hardisk"
date: 2007-10-25
forum: General Help
---

### Post by Jbs63 on 2007-10-25
hey i dont know whats happened because it used to be there but i can no longer see the partition that has windows on it (i have windows vista) when i go into /media/sda1 but its obviously reading my hardisk because it booted ubuntu off it.. any ideas??

---

### Post by taurus on 2007-10-25
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by Jbs63 on 2007-10-25
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09bf09be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37748   303204352    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           37749       38913     9357862+  83  Linux

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8cca8cca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1275    10240000    c  W95 FAT32 (LBA)

---

### Post by taurus on 2007-10-25
> **Jbs63 said:**
> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09bf09be

   Device Boot      Start         End      Blocks   Id  System
**[COLOR="Blue"]/dev/sda1   *           1       37748   303204352    7  HPFS/NTFS[/COLOR]**
Partition 1 does not end on cylinder boundary.
/dev/sda2           37749       38913     9357862+  83  Linux

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8cca8cca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1275    10240000    c  W95 FAT32 (LBA)

It's still there.  How do you mount /dev/sda1, from /etc/fstab?

```
cat /etc/fstab
```

---

### Post by Jbs63 on 2007-10-25
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=6df6a461-1122-4f31-be63-8b9ce95f3dfb /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=9824FAE924FAC970 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=634970F225AE6650 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

it looks like its there but how do i get to it?? :P im a bit new at this..i know it used to be in /media/sda1

---

### Post by taurus on 2007-10-25
What happens when you run these commands from a terminal?

```
sudo mount -t ntfs /dev/sda1 /media/sda1
sudo ls -la /media/sda1
```

---

### Post by Jbs63 on 2007-10-25
jonathan@jonathan-desktop:~$ sudo mount -t ntfs /dev/sda1 /media/sda
[sudo] password for jonathan:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda ntfs-3g defaults,force 0 0

ill try choice one and retry your commands and see what happens

---

### Post by taurus on 2007-10-25
Okay, this is what you need to do.  

Boot into Windows and shut it down properly.  Don't put it to hibernate or anything like that.  Then, reboot into Ubuntu and it should mount fine now.

---

### Post by Jbs63 on 2007-10-25
Yea that was my problem.. Thanks alot..

---

