---
title: "Cannot mount volume..."
date: 2008-03-18
forum: General Help
---

### Post by Firehalk on 2008-03-18
Hi,

I'm using the latest version of Ubuntu and when I click to open a CD (the icon of the cd-drive is create when I insert the CD) it says:

```
Cannot mount the volume
```

I tried running as ROOT, but also the same problem.

When i did try to the console, i received:

```
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I just want to read the contents of the CD and open them, not burning or anything, so why this message appears?

On Windows Vista all works fine. Any idea?

Thanks

---

### Post by matey3 on 2008-03-18
I am no expert but it seems like the CD was not closed may be after burning?
sometimes if you leave the CD open to write stuff on it later it will be read only on the machine it was burnt on (and the OS used) but not on other machines/OSes?

I put an XP CD in my Ubuntu server a few minutes ago and it mounted it fine. the read only stuff is normal cuz you cant write on the cd in most cases any ways.
hope someone with more info can help...

---

### Post by Firehalk on 2008-03-18
Well, what I know about multi-session disks is that the first time u burn it and opened the multi-session, those files should be accessed by any driver. Just those other files (added later, on a second burning) that may have some conflict with reading in some cases.

But yes, it's a multi-session disk. The computer is the same (same hardware stuff), just I burned it on Windows Vista and now i'm opening (trying to) on Ubuntu.

Didn't test other CDs, will test later (currently on Vista) but there is no way of make Linux read those CDs? Should read at least the first files I've burned.

Edit: not CDs, DVDs (if this makes any differences)

Thanks

---

