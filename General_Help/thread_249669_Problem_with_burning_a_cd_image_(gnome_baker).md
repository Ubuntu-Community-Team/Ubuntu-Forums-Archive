---
title: "Problem with burning a cd image (gnome baker)"
date: 2006-09-02
forum: General Help
---

### Post by Grog140 on 2006-09-02
I can't burn any images for some reason. I downloaded the recent knot 2 release of edgy and wanted to put it on a cd. I usually use gnome baker but it is not working for whatever reason. I also tried K3B though and I was unable to select a device in the popdown menu (there were no devices there.

When I try and burn an image with gnome baker this is what it lists as an output:

```
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.15-26-686
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hda'
devname: '/dev/hda'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Error trying to open /dev/hda exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Permission denied)... retrying in 1 second.
cdrecord: Permission denied. Cannot open '/dev/hda'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord: 
cdrecord: For more information, install the cdrtools-doc
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

```

I am not sure what to make of it.

Thanks

---

### Post by ispmarin on 2006-09-02
Are you member of the cdrom group?

---

### Post by orb9220 on 2006-09-02
For iso's I just right click the iso file in gnome and select write cd or dvd. You don't need to run an app just to burn an iso file.

---

### Post by Grog140 on 2006-09-03
I didn't know of that. I will use it once I figure out what is wrong.

It said an error occured while writing as well though.

I am 99% sure my cd drive is not broken.

EDIT: I was able to right click and write to cd if I open nautilus as root. It seems like I don't have permission to write to a cd as a non-root user.

---

### Post by ispmarin on 2006-09-03
Try to see if you are member of the cdrom group. 

sudo vi /etc/group
search for cdrom, and look if your username is in front. If it is not, then

sudo adduser <username> cdrom

Else, can you mount and access the files on a regular cd without problem? Is the gnome automont on? (System -> Removable media) If it is, try to disable, remove the cdrom, insert it again, and try to record again. Sometimes the automount does not let you access the drive with another program.

Hope it helps.

---

### Post by orb9220 on 2006-09-03
You can also copy a disc or make an iso with right click in gnome.

---

