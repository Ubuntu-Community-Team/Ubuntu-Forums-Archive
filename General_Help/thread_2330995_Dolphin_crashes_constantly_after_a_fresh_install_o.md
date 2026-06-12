---
title: "Dolphin crashes constantly after a fresh install of Kubuntu 16.04"
date: 2016-07-17
forum: General Help
---

### Post by bogdanbiv on 2016-07-17
Kubuntu version:
```
lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04 LTS
Release:        16.04
Codename:       xenial

uname -a
Linux bivdesk01 4.4.0-28-generic #47-Ubuntu SMP Fri Jun 24 10:09:13 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

Dolphin crash, from krash wizzard, with debug symbols: [http://pastebin.ubuntu.com/19738186/](http://pastebin.ubuntu.com/19738186/)
 


User home was kept from older Ubuntu 15.04, and many other Kubuntu versions before that.

---

### Post by timgood on 2016-07-19
Try renaming the folder .kde to .kdeold and .local/dolphin to .local/dolphin.old and restarting. If Dolphin still crashes you can then be pretty sure that it is something other than files in your home directory causing the problem. If you need to you can bring the older files back one at a time to see which is causing the problem. Hope this helps.

---

