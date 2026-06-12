---
title: "Windows 98 support?"
date: 2007-05-08
forum: General Help
---

### Post by CSMatt on 2007-05-08
I don't know if anyone has asked this already, but is support for a Windows 95/98/ME frontend planned?  If not, how can I use the Lupin backend with Windows 98?

---

### Post by tuxcantfly on 2007-05-08
our current version's vfat support (win9x filesystem) is kinda broken (we'll have it fixed eventually, hopefully soon), but the older versions supported it fine. Try out [http://cutlersoftware.com/ubuntusetup/wubi/downloads/experimental/wubi-7.04-minefield2.exe](http://cutlersoftware.com/ubuntusetup/wubi/downloads/experimental/wubi-7.04-minefield2.exe) (the old version), it might just work...

---

### Post by CSMatt on 2007-05-08
So Wubi works with Windows 98 unmodified?

I thought there would have to be some sort of modifications made so that it at least works with the 9x bootloader.

---

### Post by ago on 2007-05-09
Even testing1 should work with win 98 as well, but you need to make sure that the virtual drives are 4GB or less. At the moment we cannot detect fat file systems and restrict the size automatically.

---

