---
title: "SBackup restore problem"
date: 2007-01-27
forum: General Help
---

### Post by zafo on 2007-01-27
I backed up my entire system to an external USB hard drive using SBackup.  I am trying to restore a directory using Simple Backup Restore, but cannot do so.  

Restore lets me navigate to the source folder /media/usbdisk and select the backup.  I can also select the folder or files to restore.  When I click on the Restore button, a small window pops that says "Restoring..." with a light bulb icon.  If it is a directory, it just locks up after that (I've let it work on 50 MB directories for 12+ hours with no results).  I have been able to restore single files (jpeg photos) but it takes an hour or more for each one.

I have an HP with AMD X2 4600+ processors, 2 GB memory, 250 GB hard drive (external USB drive is 300 GB), running Ubuntu 6.10.  SBackup is version .10.

Anyone have any ideas on how to get this to work right?

Thanks
Rod

---

### Post by dcstar on 2007-01-27
> **zafo said:**
> I backed up my entire system to an external USB hard drive using SBackup.  I am trying to restore a directory using Simple Backup Restore, but cannot do so.  

Restore lets me navigate to the source folder /media/usbdisk and select the backup.  I can also select the folder or files to restore.  When I click on the Restore button, a small window pops that says "Restoring..." with a light bulb icon.  If it is a directory, it just locks up after that (I've let it work on 50 MB directories for 12+ hours with no results).  I have been able to restore single files (jpeg photos) but it takes an hour or more for each one.

I have an HP with AMD X2 4600+ processors, 2 GB memory, 250 GB hard drive (external USB drive is 300 GB), running Ubuntu 6.10.  SBackup is version .10.

Anyone have any ideas on how to get this to work right?

Thanks
Rod

In a terminal, run ```
dmesg
``` when you are trying to restore a file and see if any strange messages appear - there could be something in your hardware causing an issue.

---

### Post by zafo on 2007-02-02
Sorry for the slow reply - it's been a busy week.  I did a dmesg and found the lines about the USB hard drive, but some nothing unusual.  I also removed all USB peripherals except the USB mouse and so no improvement.  

Data transfer rates are fine for copying files from main hard disk to the USB hard disk, and vice versa.  And srestore *does* work - taking about 2 hours to transfer a 1.8 MB file...  I've done three jpeg files this way, but this is obviously impractical. 

zafo

---

