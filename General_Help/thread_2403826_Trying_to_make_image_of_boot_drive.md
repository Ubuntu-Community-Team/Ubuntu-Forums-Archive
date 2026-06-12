---
title: "Trying to make image of boot drive"
date: 2018-10-16
forum: General Help
---

### Post by slowjim on 2018-10-16
I installed Ubuntu 18.04 on my 250GB SSD and it runs great! I also have a 1 TB drive and I created two partions, one partion I plan to use to put an image of my SSD in case of problems. I used the program 'Disks' that came with Ubuntu. In the menu, I picked 'Create Disk Image' and attempted to save an image of my SSD to a partition on my other drive.

I get the follow error;
Error unmounting filesystem
Error unmounting /dev/sda2: target is busy (udisks-error-quark, 14)

So, does anyone know how 'Disks' can be used to make an image of the boot drive?

Thanks

---

### Post by Andrew_Benjamin on 2018-10-16
download a copy of Clonezilla.  This will make a full backup which you can restore.  It can be stored/written to a directory on the 1TB drive.  Better yet, the backup files can be made into an ISO and written to a CD/DVD which is self booting for restoring a backup.

Andrew

---

### Post by slowjim on 2018-10-16
Thanks, that worked fine and did exactly what I wanted.

---

