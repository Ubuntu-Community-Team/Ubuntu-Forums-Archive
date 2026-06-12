---
title: "FSTAB cd/dvd rom and encodings"
date: 2008-03-02
forum: General Help
---

### Post by vadviktor on 2008-03-02
My problem is as follows:

I have burnt all my 400 dvd-s under windows, with nero. Windows can always read my hungarian encoding right (&#337;úóüáé). When I automount the dvds with fstab, I have ?-mark instead of those special chars.

My fstab line:

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec    0       0

I have tried to append the utf8, or the iocharset=8859-2 options, none of them helped.

I wish for a general idea why linux cannot find the correct codepage for some dvd-s. Thanks for the help!

---

### Post by davec64 on 2008-03-02
Hi, I'm not hot on FSTAB, but have you thought of adding LOCALE into your line in FSTAB to correspond with your Hungarian encoding?

Just a thought, might be worth a go!

---

### Post by vadviktor on 2008-03-03
Hi!

Well I'm not a geek either ^^ Could you give me a clue where to look for this LOCALE feature for the fstab? My system's locale has the hungarian locale.

---

