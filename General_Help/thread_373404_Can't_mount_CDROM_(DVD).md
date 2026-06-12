---
title: "Can't mount CDROM (DVD)"
date: 2007-03-01
forum: General Help
---

### Post by Jupp on 2007-03-01
Hi,

I'm running Kubuntu 6.10 on a Intel Pentium D, Asrock 775 Dual VSTA board. 2 Sata1 HD drives, 2 GB Ram, IDE DVD RW LG GSA H12L (hda - working!) and one DVD Rom LG GSA 4082B (scd0 - seen in HAL device manager, but not accessible). The device is mounted as ide-scsi emulation in menu.lst (grub) as ... hdc=ide-scsi. ide-scsi is loaded in module.
cdrecord -scanbus gives:
scsibus3:
3,0,0 300) 'HL-DT-ST' 'DVDRAM GSA-4082B' A201' 'Removeable CDROM'
...
3,7,0 307) *

It seems, that the device is recognized.
fstab contains:
dev/hda /media/cdrom0 auto user,atime,auto,rw,dev,exec,suid 2 2
/dev/scd /media/cdrom1 auto user,atime,auto,r,dev,exec,suid 2 2

eject /dev/scd0 works and ejects the dvd.
If tried several medias and got as Sudo: 

mount -t iso9660 /dev/scd0 /media/cdrom
-> media not found

/media contains only:
(link) cdrom
cdrom0 -> from IDE DVD RW
floppy .. usb and so on.
I don't get mount points for the second device.
Additionally: This device was built in after the installation of Kubuntu (Kubuntu is the only operating system on this computer, windows runs in vmware emulation)

Another question: how can I permantly speed up the DVD Ram speed (hdparm )?

Thanx in advance for your help,
bye

---

### Post by angryfirelord on 2007-03-01
Since you only have a cdrom0 folder, make a cdrom1 folder (*sudo mkdir /media/cdrom1).*When you mount it, you only need to declare either the drive or the folder (ex. sudo mount /media/cdrom1).

Once cdrom1 is created, the command *sudo mount -t iso9660 /media/cdrom1* should work, but if it doesn't, change /dev/scd to dev/scd**0**.

---

### Post by Jupp on 2007-03-26
Thanks,

now I get access to the drive.

---

