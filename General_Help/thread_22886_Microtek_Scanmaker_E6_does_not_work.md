---
title: "Microtek Scanmaker E6 does not work"
date: 2005-03-30
forum: General Help
---

### Post by mcptron on 2005-03-30
Has anyone a working ScanMaker E6 under Hoary?
[http://www.sane-project.org/sane-mfgs.html#Z-MICROTEK](http://www.sane-project.org/sane-mfgs.html#Z-MICROTEK) says that it is supported. It is connected via an Adaptec 2940 SCSI controller.

The Scanner works fine on the same machine under SuSE 9.2, but Sane does not find the device under Hoary.

Any ideas?

thx.
mike

---

### Post by scarecrow on 2005-03-31
sudo sane-find-scanner on a console
What's the output?
If the scanner is not there then install the sane backends package.

---

### Post by mcptron on 2005-03-31
So here is what I found out:

sane-find-scanner has the following output when run as root:

found SCSI scanner " Scanner 600 1.70" at /dev/sg0
found SCSI scanner " Scanner 600 1.70" at /dev/sg1
found SCSI scanner " Scanner 600 1.70" at /dev/sg2
found SCSI scanner " Scanner 600 1.70" at /dev/sg3
found SCSI scanner " Scanner 600 1.70" at /dev/sg4
found SCSI scanner " Scanner 600 1.70" at /dev/sg5
found SCSI scanner " Scanner 600 1.70" at /dev/sg6
found SCSI scanner " Scanner 600 1.70" at /dev/sg7
found SCSI scanner " Scanner 600 1.70" at /dev/sg8
found SCSI scanner " Scanner 600 1.70" at /dev/sg9
  # Your SCSI scanner was detected. It may or may not be supported by SANE. Try
  # scanimage -L and read the backend's manpage.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a driver for your USB host controller and have installed a
  # kernel scanner module.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

scanimage -L tells me that it is a microtec scanmaker E6. the multiple result entries seem to be a cause of missing lun-support of the scanners scsi interface.

the problem is: /dev/sg0 has the following access rights:

crw-rw----  1 root disk 21, 0 Mar 31 11:04 /dev/sg0
and a  normal user is not in the disk group - even when marked to have scanner device access in the user admin application.

a chmod o+rw /dev/sg0

solves the problem until the next reboot (because of udev, i think). sane works fine then until the access permissions are reset to the old values.

how can i fix this permanently without an automatic chmod hack at startup time?

thx. & rg.
mike

---

### Post by kleeman on 2005-03-31
Quick hack:

Create /etc/init.d/local 

Put #! /bin/sh on the first line

then on the second line put the command you want to execute when you login.

---

### Post by kleeman on 2005-03-31
Oh sorry I read your post and you didn't want a quick hack...

---

### Post by mcptron on 2005-03-31
did it that way now. but to get it work i needed to add a S99local -> ../init.d/local symlink to /etc/rc2.d.

i'm doing now a chgrp scanner /dev/sg0 at startup. i think this could be a bug. /dev/sg* should already have this owner group.

thanx and rg.

mike

---

### Post by scarecrow on 2005-04-04
[QUOTE=mcptron]did it that way now. but to get it work i needed to add a S99local -> ../init.d/local symlink to /etc/rc2.d.

i'm doing now a chgrp scanner /dev/sg0 at startup. i think this could be a bug. /dev/sg* should already have this owner group.

thanx and rg.

mike[/QUOTE]
 Not having an Ubuntu in front of me right now, but when sane is installed it creates a usergroup "scanner". Add your user to that group to be able to operate your scanner with non-root priviledges.

---

### Post by reneaguirre on 2005-04-29
Had a similar problem with a HP flatbed scanner model C5111A, in order to make udev to assign proper privileges (to *proper* devices) you must edit your /etc/udev/rules.d/udev.rules and set a new rule (or modify an existing one). In my case I had to add something like:

# permision for HP SCSI scanner
BUS="scsi", KERNEL="sg0", SYSFS{model}="C5110A", SYSFS{type}="3", NAME="%k", MODE="0666", GROUP="scanner", SYMLINK="scanner"

To find out the SYSFS{model} and SYSFS{type} info, just typed this:
udevinfo -a -p /sys/class/scsi_generic/sg0/

and checked the output for proper scsi information.

Check this out:
[http://webpages.charter.net/decibelshelp/LinuxHelp_UDEVPrimer.html#udevrules](http://webpages.charter.net/decibelshelp/LinuxHelp_UDEVPrimer.html#udevrules)

There's also a /etc/udev/permissions.d/udev.permissions file to set device permisions, but as the previous did work I didn't continued searching for information.

Regards.

---

