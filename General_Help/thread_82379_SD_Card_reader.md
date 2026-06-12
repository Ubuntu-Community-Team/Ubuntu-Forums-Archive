---
title: "SD Card reader"
date: 2005-10-26
forum: General Help
---

### Post by 3dmaker on 2005-10-26
Hello all. I have a Compaq Presario R3000 laptop with Ubuntu 5.10 (GNOME). It has a built in SD Card reader. Ubuntu does not see it. And I need to mount a SD Card. My FSTAB only has like /hda1 and /hda2 /floppy and /cdrecoder. 
No SD. How do I mount it?

---

### Post by pisuke on 2005-10-26
Are you sure your Card reader is supported in Ubuntu? 

I'm not sure but sometimes that kind of devices are not well supported.

Good luck.

---

### Post by frenkel on 2005-10-26
Built-in SD Card readers aren't supported in Linux (yet). It's a closed format and very hard to reverse engineer.
You can however, buy a USB SD Card reader, as those work very well with Linux (and Ubuntu).

---

### Post by ibanez88 on 2005-11-16
[QUOTE=frenkel]Built-in SD Card readers aren't supported in Linux (yet).[/QUOTE]

Are you sure that that's accurate?  Winbond SD slots are supported in the 2.6.14 kernel (current stable version).  I've heard of other makes working out of the box also.

Unfortunately I have not been able to get the built-in SD working on my Averatec 1050-EB1 yet.  I somehow think that a large part of it may be my fstab which I simply haven't gotten around to figuring out yet.

Has anyone used the Winbond driver or any other built-in SD successfully?  Does it require a fstab entry?  (hmmm might be a question for the WBSD mailing list)

---

