---
title: "K3B Error burning ISO"
date: 2013-02-09
forum: General Help
---

### Post by SuperFreak on 2013-02-09
I am trying to burn an image of CAINE (a Forensic OS for Linux) but get errors when burning Verbatim DVD R+ discs.
This is the error(approximately) for K3B:
```
cd record returned an unknown error 254 sometimes writing TAO will fix this
```
This is the error for Brasero:
```
SCSI error on write(52848,16): See MMC specs: Sense Key B "Command aborted", ASC 00 ASCQ 00
```
I have tried burning at 8X instead of auto. I have wasted 4 discs as a little gets written and then I get the error message.

---

### Post by scdbackup on 2013-02-10
Hi,

> SCSI error on write(52848,16): See MMC specs: Sense Key B "Command aborted",
> ASC 00 ASCQ 00

This error message stems from libburn, of which i am the developer.
It got the SCSI error code "B 00 00" as reply from the system call
ioctl(SG_IO). This error code is most probably issued by the operating
system and not by the drive.

The reason for this might be that the drive did not report the completed
execution of the WRITE10 command within a reasonable time. (One would have
to dig in the kernel code to find more candidates which trigger this error.)


Unsatisfying advice:

Try a different media type (e.g. DVD-R) or a different drive.

The problem might be volatile.
A single successful burn run will not guarantee that it is solved.
(Such volatile success and failure often leads to false theories
 that a particular burn program is to blame. Not that i deem my
 software free of bugs, but i would doubt such a theory if it is
 based on SCSI error key "B".)


Have a nice day :)

Thomas

---

### Post by SuperFreak on 2013-02-10
Thanks, although I don't know what to do now . The drive was $13 so no great loss to replace it. I just tried ripping a CD and it works fine. I believe I made a bootable copy of 12.04 on it some time ago without issue. 
I guess most people use USB keys to copy media now.

---

### Post by scdbackup on 2013-02-10
Hi,

only further experiments could show the difference between a dying
drive and indigestible media..

> I guess most people use USB keys to copy media now.

Optical media are still cheaper. The main competition for backup
purposes are portable hard disks, though. Hard to beat in any aspect
except heavy mechanical impact.

Have a nice day :)

Thomas

---

### Post by SuperFreak on 2013-02-13
Replaced the DVD burner(only 10 moths old) with new and it works now. Will marked this solved

---

