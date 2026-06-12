---
title: "Structure Needs Cleaning error for external hard disk"
date: 2018-08-01
forum: General Help
---

### Post by dkepesh on 2018-08-01
I have a WD external hard drive. I plugged it into my desktop and got "Error mounting", saying "Structure Needs Cleaning." I tried to correct the error by running:

[INDENT][FONT=courier new]sudo fsck.ext4 /dev/sdb1[/FONT][/INDENT]


and got many pages of output/prompts that looked like this:

[INDENT][FONT=courier new]Group 180's inode bitmap at 30644533 conflicts with some other fs block.[/FONT][/INDENT]
[INDENT][FONT=courier new]Relocate<y>? yes[/FONT][/INDENT]


The data on the disk is not important to me; I just want the disk to be functioning so I can put new data on there. Thus I ran:

[INDENT][FONT=courier new]sudo fdisk /dev/sdb[/FONT][/INDENT]


and deleted the one and only partition on the disk, created a new empty GPT disklabel with just a single partition, "verified" the partition table and "wrote" it. Then I formatted the one and only partition on the disk ext4.

To check if there were any errors on the disk, I ran:

[INDENT][FONT=courier new]sudo smartctl -d sat -a /dev/sdb[/FONT][/INDENT]


It had none! Is there anything that I am missing? I am about to make this my primary hard disk--I want to make sure (as much as possible) that the disk and data will be safe. Thanks!

---

### Post by SeijiSensei on 2018-08-02
"Structure needs cleaning" is an error associated with XFS filesystems, not ext4 ones. If you reformatted the device, you should be fine.

---

### Post by gldneagl on 2019-02-23
> **SeijiSensei said:**
> "Structure needs cleaning" is an error associated with XFS filesystems, not ext4 ones. If you reformatted the device, you should be fine.

Okay, but I've been building Linux systems now for over 22 years, and on USB for over half of that, and with the exception of builds at work for Redhat (and clones, including Oracle) I never use XFS...

and I have been getting this same error "Structure needs cleaning" over deleted files for months on USB based builds of Ubuntu-Mate 16 inside the squashed casper-rw filesystem from a custom build that I first roll into an ISO and then punch into the USB stick with mkusb.

Maybe I'm asking this question the wrong place, but are one of these programs using XFS and I didn't know?

---

