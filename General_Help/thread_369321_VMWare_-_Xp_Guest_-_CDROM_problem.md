---
title: "VMWare - Xp Guest - CDROM problem"
date: 2007-02-24
forum: General Help
---

### Post by Tazix on 2007-02-24
Running Xubuntu Edgy... VMWare Player installed via Automatix.

XP image created on XP machine with VMWare Workstation.  VMWare tools installed.

Copied image to Xubuntu Box, everything works in Xubuntu's VMware Player except access to the CDROM.

**Error: Unable to open host CD-ROM drive "D:" No such file or directory.  Virtual device ide1:0 will start disconnected.**

At first I thought it might be a mount issue... so I popped in a CD which automounted before running VMPlayer.  Same error.

Both machines have the hard drives and optical drives on the same IDE channels. (Hard drive on 0:0, optical drive on 1:0)

It's obviously looking for a file or directory called "D:"

Anybody know what I need to do to edit my .vmx file to correct this situation?

Thanks,

-Taz

---

### Post by Tazix on 2007-02-24
Ok... got it fixed by posting on the VMWare forums:

[http://www.vmware.com/community/thread.jspa?threadID=73747&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=73747&tstart=0)

Basically had to change the line in the VMX from:

*ide1:0.fileName = "D:" *

to:

**ide1:0.fileName = "/dev/cdrom" **

and change the line from:

*ide1:0.deviceType = "cdrom-raw" *

to:

**ide1:0.deviceType = "atapi-cdrom"**

-Taz

---

