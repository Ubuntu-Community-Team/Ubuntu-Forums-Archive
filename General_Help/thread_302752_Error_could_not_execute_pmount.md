---
title: "Error: could not execute pmount"
date: 2006-11-19
forum: General Help
---

### Post by mexp on 2006-11-19
](*,) 

Can't get cdrom mounted on Breezy... It's an old box, PII with 256 MB of ram, so I'm not so keen on updating it. 

But recently for some reason I can't access the cdrom. The error I get is

[INDENT]Warning: device /dev/hdc is already handled by /etc/fstab, supplied label is ignored
mount: I could not determine the filesystem type, and none was specified
Error: could not execute pmount[/INDENT]

I found out there was a bug with pmount in dapper, and I updated it to version 0.9.6-1. That didn't help.

Tried tinkering with fstab, and changed the entry for cdrom like this:

[INDENT]#/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom0   auto    user,noauto     0       0[/INDENT]

Command line mount gives this:

[INDENT]sudo mount -t iso9660 /dev/hdc /media/cdrom
mount: No medium found[/INDENT]

The cd works on other Ubuntu box, it only has jpeg images on it.

The automount doesn't work for floppy either, but I can mount a floppy with
[INDENT]
sudo mount -t vfat /dev/fd0 /media/floppy[/INDENT]

I even tried changing the cdrom drive, but that won't do the trick either. Am I at the end of the road???

:confused:

---

### Post by mexp on 2006-11-27
pmount... anyone... pmount???

---

### Post by ssavelan on 2006-12-21
yes pmount.... how do you read ntfs windows partitions... samba?  err...](*,) 

just trying to open my SCSI drive from places... could not execute pmount

---

