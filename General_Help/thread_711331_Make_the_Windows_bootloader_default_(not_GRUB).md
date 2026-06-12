---
title: "Make the Windows bootloader default (not GRUB)"
date: 2008-02-29
forum: General Help
---

### Post by breaking on 2008-02-29
For a while now I have had a dual boot Ubuntu 7.10 (Now 8.04 alpha 5) and Windows Vista system, running off one hard-drive with 3 partitions (EXT, Swap, NTFS).
Now I wish to dedicate this drive entirely to Vista, so I want to know if there is a way I can stop the PC from loading the partition with GRUB first, and ONLY use the Windows bootloader. At the moment the option in GRUB is chainload to Windows, or boot Ubuntu.

---

### Post by jeffus_il on 2008-02-29
Boot from the windows cd, run the recovery console, and run the command fixmbr, this will make any Ubuntu partitions unbootable.

---

### Post by breaking on 2008-02-29
Does that work on the VISTA recovery disk, or only the XP one? I will try. Is there a way to edit the MBR from within Windows or Linux (a 3rd party prog maybe)?

---

### Post by jeffus_il on 2008-02-29
I have no experience with Vista, I would guess that it would work, it really not part of the running OS, try it, at worst you won't find it.
There was a Bart Ultimate Boot CD, maybe you can google for a Vista one.

---

### Post by louieb on 2008-02-29
> **breaking said:**
> ...I want to know if there is a way I can stop the PC from loading the partition with GRUB first, and ONLY use the Windows bootloader. ...

Replace the IPL in the MBR code to GRUB with code that points to the VISA bootloader.   [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/") can do it. Heres my favorite page on the subject. [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

