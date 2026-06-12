---
title: "cdrom behavior"
date: 2007-04-24
forum: General Help
---

### Post by jwmwalrus on 2007-04-24
Hi,

I'm having some problems with the cdrom, though I'm not sure if those are real problems or just the expected behavior.

In many cases, when I insert a CD and browse through Nautilus, it simply shows funny symbols (e.g., Chinese or similar).  In such cases, Nautilus is never launched automatically.  The portion of fstab that corresponds to the cdrom follows:

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,utf8     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,utf8     0       0

I added the utf8 option a long time ago, because some of the filenames in my CDs have accents. The problem is usually solved by restarting the computer... But I would prefer not to have to restart every time.

Also, I noticed that it is not possible to browse music CDs through Nautilus; an error is shown when trying to access the CD.  They are available only through SoundJuicer, though...  This is a pretty old behavior so, is there any good reason for that?

Any help provided will be greatly appreciated.

John.

---

