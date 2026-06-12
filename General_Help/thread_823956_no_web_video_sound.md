---
title: "no web video sound"
date: 2008-06-09
forum: General Help
---

### Post by stretch77 on 2008-06-09
I have the Dell 1525n model with Ubuntu and Hardy. I don't have sound on video from the web. I can play CD's and DVD's fine. The effectual and startup sound work fine as well. I have searched and searched but couldn't find anyone else with the same problem. Thank you. I am using firefox 3b5 for browsing.
I have tried re-installing the flash player plug in to no avail. I have also toggled the system/preferences/sound settings from pulse to alsa to auto and got nothing.  Anyone have an idea?

---

### Post by fooman on 2008-06-09
no sound only in flash? ...is libflashsupport installed?  try this in a terminal:

```
sudo apt-get install libflashsupport
```

might have to restart firefox afterwards.

---

### Post by stretch77 on 2008-06-09
Yep libflash support has been installed, uninstalled and reinstalled.
I just caught another thread that suggested uninstalling the flash plug in and trying adobe flash 10. Sound reasonable?

---

