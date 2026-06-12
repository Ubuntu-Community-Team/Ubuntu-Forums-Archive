---
title: "can burn audio cds, can't use cdrecord...?"
date: 2005-11-01
forum: General Help
---

### Post by visctrix on 2005-11-01
Hi

I've just installed ubuntu apparently very successfully - I'm going to install it in my office too...

But I can't access my reiserfs filesystems, and I can't access my fat32 filesystems, and I can't start up Xandros, so I plan to use SystemRescueCD to rearrange some files.

Only problem is I can't burn the iso onto disk.  I have successfully copied some audio CDs using Serpentine, and if I put a blank CD into the drive the CD/DVD Burner dialogue comes up, but whatever I do I get asked to insert a blank CD into the drive.

If I open a terminal and write 

[FONT="Fixedsys"]visctrix@x1-6-00-30-bd-b1-72-6fUbuntu:~$ sudo cdrecord -scanbus[/FONT]

I get

[FONT="Fixedsys"]Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-9-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .[/FONT]

Any thoughts appreciated...

visctrix

---

### Post by allroz on 2005-11-01
Try this instead:

```
sudo apt-get install gnomebaker

killall gnome-panel
```

applications<accessories<gnomebaker

---

