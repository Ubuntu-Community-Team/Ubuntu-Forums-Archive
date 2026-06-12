---
title: "Feisty: can't read data files from DVD with upgrade or clean install"
date: 2007-04-20
forum: General Help
---

### Post by mdurham on 2007-04-20
I can't read data files from my DVD drive.
If I insert an unencoded DVD, it shows correctly on the desktop.
If I inspect the DVD with Nautilus, all files are shown correctly, types, size etc.
If I inspect one file (say a VOB) with a hex editor, all data appears as 00 Hex (zeros).
I am unable to copy files from the DVD, I get an I/O error message.

I have one 7.04 system upgraded from Edgy that originaly worked ok but now doesn't.
I also have a clean install of 7.04 that exibits exactly the same problem, i.e. can't read DVD's.
Reading/writing C/D's appears to be no problem.
I've tried DVD+RW and DVD-R with the same result.

I noticed in the clean install, the fstab file contained the line:
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
But, there is no "/dev/hdc" so I changed it to "/dev/scd0", this made no difference to the reading problem but it did mount the DVD in the correct place, i.e. "/media/cdrom0" whereas before it got mounted in "/media"

Why would the clean install use "/dev/hdc" when it doesn't exist?

Needless to say, I can't play DVD's either.
Would anyone have any ideas as to what I can try next?

Thanks, Mike

---

### Post by am_pcguy on 2007-04-21
I can't help but I have the same problem.  This bug report seems to be similar:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94119](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94119)

I can't mount a CD or DVD at all, I get mount: not a directory.

---

### Post by mdurham on 2007-04-21
> **am_pcguy said:**
> I can't help but I have the same problem.  This bug report seems to be similar:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94119](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94119)

I can't mount a CD or DVD at all, I get mount: not a directory.

Thanks am_pcguy, I just added my 2cents to the bug report.

---

