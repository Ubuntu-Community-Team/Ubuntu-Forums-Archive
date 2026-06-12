---
title: "hal.dll"
date: 2007-01-07
forum: General Help
---

### Post by baitman on 2007-01-07
Hi all,

Reinstalled ubuntu tonight and i'm having trouble editing my boot.ini. I've read several guides none of which i managed to get to work for me, i'm on edgy eft and i need to edit my boot.ini file, can any one help?

---

### Post by geek_Man on 2007-01-07
If you're trying to do it within Ubuntu, you can't. You can only read NTFS, not write to it (that is from ext3). If you're within Windows... I don't know why you wouldn't be able to.

---

### Post by SkyIsFalling on 2007-01-07
Assuming your Windows filesystem is NTFS and you're keen on editing it from within Ubuntu, you may want to check out [ntfs-3g]("http://www.ntfs-3g.org/").

Having said that, a simpler solution might be editing it from the Windows recovery console or [BartPE]("http://http://www.nu2.nu/pebuilder/").

---

