---
title: "Sbackup files not showing up on backup drive"
date: 2008-05-11
forum: General Help
---

### Post by BuckroeBill on 2008-05-11
I have been using sbackup and like he program but have done something to upset the program I backup daily to an external hard drive attached via USB. Normally I can browse that drive and see the backup files listed be date and reassure myself that the system is working. Recently the files are visible in the Backup Restore list but NOT showing on the USB Drive. Anyone got any idea what may be going on here.
System HP Pavilion dv8000
2 hd's 160 gig and 80 gig internal and one external 80 gig
2 gig ram
2.2 mgz AMD Turion processor

I'll keep looking.
Thanks

---

### Post by rbmorse on 2008-05-11
Open a terminal window and run

sudo simple-backup-config

provide your user password when prompted and then click on the destination tab and make sure that is set correctly. 

If that looks OK, then look at the "time" tab and verify that setting is correct 

You can click on "backup now" to test. Check the term window for errors.

---

### Post by BuckroeBill on 2008-05-11
Checked all my settings and al seems well. I found the backups in a folder under the /media folder. I think the designated drive got too full and the backup program saved them there. Can't think of another reason. At any rate I have cleaned out the USB drive, reformated, and started over again. I saved the old backups to my big hard drive until I no longer think they will be useful.
Thanks for your very useful recommendations. You guys are really and asset to us all.
Bill

---

### Post by eivind on 2008-05-13
A small, but important question:

Are you certain that your external disk isn't formatted as VFAT or FAT? If that is the case, you are in real danger of losing your data... Sbackup can make files larger than the 4GB VFAT limit, and in addition doesn't tell you if a backup failed. This can be critical if, like me, you try to restore backups made to an external disk.

Because sbackup currently doesn't tell you whether or not a backup was successful, I discourage using it in its current state.

---

