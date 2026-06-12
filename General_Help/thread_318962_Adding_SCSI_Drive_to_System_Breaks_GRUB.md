---
title: "Adding SCSI Drive to System Breaks GRUB"
date: 2006-12-14
forum: General Help
---

### Post by ScottCh on 2006-12-14
Hi Folks,

I have an Ubuntu Dapper system with a single SATA hard disk.  It boots the kernel and runs fine.  The hard disk is mapped to /dev/sda by the kernel.

The system also has an LSI Logic 53c895a SCSI host adapter.  I recently tried to plug a new SCSI hard disk into this controller, but when I do the system hangs while booting.  

The SCSI hard disk is terminated properly.  There is no SCSI device ID conflict.  When the SCSI controller initializes during bootup, it lists the SCSI devices that it finds.  The SCSI hard disk is listed at the expected ID, and no error is reported.

Booting proceeds up to the point where it attempts to boot the OS from CD-ROM, then the next boot device is the hard disk.  At this point the boot process hangs indefinitely, without printing anything new on the console.  If I disconnect the SCSI drive, the system boots properly again.

I tried booting from my Ubuntu CD-ROM and selected "Rescue System" from the menu.  I was able to start a shell from my disk0/partition 4 root partition.  Using fdisk -l, I was able to determine that the disk assignments have not changed.  The SATA hard disk is still /dev/sda, and the new SCSI hard disk is /dev/sdb.  fdisk has no problem listing their partition tables.

I also checked the system BIOS settings. These allow the hard drive boot priority to be specified.  The default boot priority settings seem correct.  Boot priority #1 is the SATA drive, #2 is the SCSI drive, and #3 is "Bootable PCI devices".  This looks reasonable to me.

So why does adding the SCSI drive to the system cause the boot process to hang?

I also tried the Ubuntu CD-ROM's boot option "Boot from 1st Hard Drive".  When I select this, I get a very strange result.  The console generates an endless string of round dot-shaped symbols, which goes on filling up the screen until I reboot.

Is this a diagnostic output from GRUB?

Thanks for any pointers!

--
Scott C in Cary, NC USA

---

