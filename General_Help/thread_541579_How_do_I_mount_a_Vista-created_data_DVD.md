---
title: "How do I mount a Vista-created data DVD?"
date: 2007-09-03
forum: General Help
---

### Post by mjpatey on 2007-09-03
I created a DVD of photos on a relative's Vista laptop while on vacation last week (4GB worth).  It opened just fine on another Vista laptop, but I can't get it to mount on my home PC in Ubuntu.  When I put the DVD in my drive, Ubuntu says it cannot mount the volume.

I'm running Feisty, and the drive seems fine in every other way.

Interestingly enough, if I open up a Windows XP virtual machine (not Vista) in VirtualBox, it reads the DVD fine, too.  In fact, my current workaround is to copy it from the DVD in my virtual XP install, via WinSCP, to the host OS (Ubuntu)... and it's working like a charm (albeit a slow one).  I'd like to know, though, if anyone knows of a real way to mount a Vista-created data DVD in Ubuntu.

Thanks for any help you may have!

-Mark

---

### Post by wolfen69 on 2007-09-03
the only thing i can think of is that vista created the photos in a format that ubuntu cant recognize. was it a specialized program that you used to create the dvd?

---

### Post by mjpatey on 2007-09-03
No, they were straight from my camera (a Canon Digital Rebel XTi), and mostly regular old jpegs, copied the usual way from the HD to the DVD drive.

Thanks, though!

---

### Post by tlutz on 2007-10-22
I've been having problems mounting a DVD I created in XP, with over 4GB of data on it.

This has been incredibly frustrating, and I still have not found a solution.

I can access the DVD fine in my Windows XP virtual machine.

I originally thought this was related to the 4GB inode limit, but found this was addressed in an earlier kernel version (2.6.8 I believe).

I repeatedly ejected and tried remounting the DVD, and eventually it worked. I continually checked the output of dmesg and saw several errors.

[17539.028998] UDF-fs: No VRS found
[17540.097365] ISO 9660 Extensions: Microsoft Joliet Level 3
[17540.098002] ISOFS: changing to secondary root
[18037.675982] hda: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[18037.675989] hda: media error (bad sector): error=0x34 { AbortedCommand LastFailedSense=0x03 }
[18037.675992] ide: failed opcode was: unknown
[18037.676465] hda: error code: 0x70  sense_key: 0x03  asc: 0x02  ascq: 0x00
[18037.676473] end_request: I/O error, dev hda, sector 404

Maybe this is the case of a flaky DVD? Maybe Linux isn't as friendly with flaky DVDs as Windows?

---

### Post by SonicSteve on 2007-10-25
It's probably because Vista formatted them with UDF iso-13346 version of encoding. There is a patch for supporting this on sourceforge but it means compiling a new linux kernel.

---

### Post by UK-Wobbie on 2007-10-25
> **mjpatey said:**
> I created a DVD of photos on a relative's Vista laptop while on vacation last week (4GB worth).  It opened just fine on another Vista laptop, but I can't get it to mount on my home PC in Ubuntu.  When I put the DVD in my drive, Ubuntu says it cannot mount the volume.

I'm running Feisty, and the drive seems fine in every other way.

Interestingly enough, if I open up a Windows XP virtual machine (not Vista) in VirtualBox, it reads the DVD fine, too.  In fact, my current workaround is to copy it from the DVD in my virtual XP install, via WinSCP, to the host OS (Ubuntu)... and it's working like a charm (albeit a slow one).  I'd like to know, though, if anyone knows of a real way to mount a Vista-created data DVD in Ubuntu.

Thanks for any help you may have!

-Mark

So you like to mount it? Get AcetoneISO2 It will play your DVD Images :D
[http://www.acetoneteam.org/central.html](http://www.acetoneteam.org/central.html)

---

### Post by pete.dawgg on 2007-11-14
so that's the punishment for using non-standard-compliant software. you're lucky this is not more important data. ;)

try to mount the disk by hand and read the errormsg.("filessysrtwem blbla not supported by kernel " or sth).
it may have been written with packet-writing software,  which linux does not support (fully) yet. maybe you just need to load another module.

---

