---
title: "Need help to add NTFS winxp partition"
date: 2004-10-30
forum: General Help
---

### Post by ToWAH on 2004-10-30
Hi m8s well in my second day , i just resolved the compiler problems with gcc hehe.
Well i like to add a winxp partition 160 GB disk but i dont know how to do i read a bit about it but im messed up :|
im cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

and a last problem, how i must do to import windowsxp fonts here ?
thanks in advanced m8s

---

### Post by jdong on 2004-10-30
Do you know the name of the partition? is it a separate hard drive? Or just a separate partition?

---

### Post by ToWAH on 2004-10-30
[QUOTE=jdong]Do you know the name of the partition? is it a separate hard drive? Or just a separate partition?[/QUOTE]
a separate HDD

---

### Post by ToWAH on 2004-10-30
ok i solved myself , well the winxp HDD its a seagate sata 160 Gb but i dont know what /dev/ ? so i did: 
cat /var/log/kern.log
and i found it :D
Oct 29 07:47:17 localhost kernel:   Vendor: ATA       Model: ST3160023AS       Rev: 3.05
Oct 29 07:47:17 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 05
Oct 29 07:47:17 localhost kernel: SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
Oct 29 07:47:17 localhost kernel: SCSI device sda: drive cache: write back
Oct 29 07:47:17 localhost kernel:  /dev/scsi/host0/bus0/target0/lun0: p1
Oct 29 07:47:17 localhost kernel: Attached scsi disk sda at scsi0, channel 0, id 0, lun 0

hehe 
fdisk /dev/sda
p to print partitionThe number of cylinders for this disk is set to 19457.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End   The number of cylinders for this disk is set to 19457.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

mkdir /mnt/winxp
mount -t ntfs /dev/sda1/mnt/winxp
now i can read windowsxp HDD

suddenly appears a popup windows saying that u cannot access bla bla bla
well now only need add in /etc/fstab



#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none         # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
   swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/fstab 

something like this :



/dev/sda1 /mnt/winxp ntfs ro,user,umask=0 1 0

but its possible write in nfts rw instead ro atributte , or i will destroy it ?

---

