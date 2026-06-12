---
title: "No Partitions shown in Ubuntu!!!! pleez HELP!"
date: 2008-03-17
forum: General Help
---

### Post by Sabeeh on 2008-03-17
Hey fellas, i'm a newbie and there's a bit ov a problem..

I recently installed ubuntu 7.10 Gusty Gibbon on an XP machine, it all went well until recently one day my dad, who just loves windows (it wasn't suppose to mention), booted in XP, and from that day onwards there're no partition shown in my Ubuntu desktop or in Computer..

Here is the fdisk -l result:
<vB>Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc544c544

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        8832    50460165    f  W95 Ext'd (LBA)
/dev/sda3            8833        9696     6940080   83  Linux
/dev/sda4            9697        9729      265072+  82  Linux swap / Solaris
/dev/sda5            2551        5100    20482843+   7  HPFS/NTFS
/dev/sda6            5101        8832    29977258+   7  HPFS/NTFS

</vB>

 and here's is the fstab result 

<vB># /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=0444eb29-2ff5-4dd9-8f4b-bf18f8839e00 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=D088BF2F88BF1348 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=7A32D0D332D0958B /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=5A82F31082F2EEFF /media/sda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=cdfef6da-60cf-422b-b9f6-d9c736d57db1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
</vB>

i really dont know what that means, but it think it will definitely help you guys.

---

### Post by jeffus_il on 2008-03-17
A Guess!
Open a terminal and run ```
gconf-editor
```
Under /apps/nautilus/desktop
Is volumes_visible checked?

---

### Post by Sabeeh on 2008-03-17
yes, they are checked....

---

### Post by sisco311 on 2008-03-17
Can you mount manually the partition?
```
sudo mount -t ntfs -o defaults,umask=007,gid=46 /dev/sda1 /media/sda1
```

---

### Post by Sabeeh on 2008-03-17
this was the output:

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0

---

### Post by sisco311 on 2008-03-17
You need to boot into Windows and shut it down properly.(don't use hibernation)

---

### Post by Sabeeh on 2008-04-14
Yup..it solved it..is there a way to automatically boot them at startup...ignore the Log file that indicates an unclean shutdown...are there any pros and cons?? if so plz tell me something.

---

