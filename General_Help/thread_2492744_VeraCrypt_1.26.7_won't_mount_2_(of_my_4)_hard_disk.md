---
title: "VeraCrypt 1.26.7 won't mount 2 (of my 4) hard disks"
date: 2023-11-21
forum: General Help
---

### Post by martinb105 on 2023-11-21
Today I attempted to "Auto-Mount Devices" to access 4 of my drives, just as I've been doing for years.

/dev/sdb and /dev/sdd both mounted, but /dev/sdc or /dev/sde did not mount (all volumes share the same password).

I tried to mount sdc and sde individually via the "Mount" button, but both gave the same error:
>  Operation failed due to one of the following

 - Incorrect password
 - incorrect volume PIM number
 - incorrect PRF (hash), or
 - not a valid volume.
I've tried this multiple times, also trying to use the backup embedded header, but it always gives the same error.

The only difference I can think of between these drives is that the two failing volumes were probably created some years before the two that are still working.

So I checked my Ubuntu update logs, which is where I found that VeraCrypt 1.26.7 was installed last night.

So I removed VeraCrypt 1.26.7 and found an older 1.25.4 deb package online to try.  Now all 4 drives can be mounted and accessed again!

To be honest, I'm kinda terrified of updating VeraCrypt now out of fear of losing my data.

Is this a known issue and is there anything that can be done to mitigate against it? (besides the obvious like making backups that *don't* use VeraCrypt)

Cheers!

---

### Post by MAFoElffen on 2023-11-23
I would post on the [VeraCrypt Forum]("https://sourceforge.net/p/veracrypt/discussion/")... I think that is where the bug reports trace back to for VeraCrypt.

---

