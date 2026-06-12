---
title: "Former Ubuntu boot drive (USB) can't be formatted"
date: 2014-12-15
forum: General Help
---

### Post by 863-wilkinson on 2014-12-15
I have a 16 GB flash drive that I used as an Ubuntu live disk some  months ago.  Now it's become corrupted somehow and I can't format it or  edit partitions.  Is there a way to force it to format?  The drive is  unusable as-is and I'm hoping I can rescue it.  The partitions on there  are:

/dev/sdb1  1.0 GB Unknown
/dev/sdb2  2.4 MB FAT-12
Free space 15 GB


The error messages I get are:

**Error formatting disk**
Error synchronizing after initial wipe: Timed out waiting for object (udisks-error-quark, 0)

**Error when I try to boot from the disk**
*[Something to the effect of] *Could not find a live filesystem.

**If I plug the drive into a Windows computer**
*[No error message, but] *F: USB Memory Device (16.0 kB free of 2.4 MB) *[instead of "15 GB free of 16 GB"]*

[B]Error deleting partition
[/B]Error deleting partition /dev/sdb1 *[or /dev/sdb2]*  : Command-line `parted --script "/dev/sdb" "rm 2"' exited with non-zero  exit status 1: Warning: /dev/sdb contains GPT signatures, indicating  that it has a GPT table.  However, it does not have a valid fake msdos  partition table, as it should.  Perhaps it was corrupted -- possibly by a  program that doesn't understand GPT partition tables.  Or perhaps you  deleted the GPT table, and are now using an msdos partition table.  Is  this a GPT partition table?
Error: Both the primary and backup GPT  tables are corrupt.  Try making a fresh table, and using Parted's rescue  feature to recover partitions.
 (udisks-error-quark, 0)[I]

[So I tried using [/I]sudo parted /dev/sdb*]*[B]

Error when I use *(parted) rescue 0 1000000000* or *(parted) rescue 1000000000 1002400000*
[/B]Warning: /dev/sdb contains GPT signatures  ... *[same as above]* ... Is this a GPT partition table?  
parted:  invalid token: 0  
Yes/No?:  [I]
[No returns me to the parted prompt;  Yes yields a further error message saying]  [/I]Error:  Both the primary and secondary ... *[same as above]*

**Error creating partition**
Error  creating partition on /dev/sdb: Command-line `parted --align optimal  --script "/dev/sdb" "mkpart primary ext2 984MiB 16009658367b"' exited  with non-zero exit status 1: Warning: /dev/sdb contains GPT signatures  ........* [same as above]*

---

### Post by oldfred on 2014-12-15
Did you use the dd method to create the Ubuntu installer. That is not a standard drive with partitions, but an image of the DVD which is bootable. But then data is in the first sector of the drive where partition table normally is, so standard partition tools try to convert random data into  a partition table.

I might zero out first sector, and since it says it also has gpt data run fixparts to zero out gpt partition table which has its backup at end of drive.
With gpt the first sector is only the protective MBR. Gpt has both partition tables after protective MBR & backup at end of drive.

Change sdX to correct drive, sdb, sdg etc. Double and triple check you have typed the correct letter a it will erase boot & partition table of the drive you specify. Any typo then creates major issues.
 Zero out MBR only, chang sdX to correct drive, erases both boot code and partition table.
dd if=/dev/zero of=/dev/sdX bs=512 count=1

      
 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

