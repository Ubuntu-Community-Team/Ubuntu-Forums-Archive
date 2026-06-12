---
title: "Kernel parameter to disable AMD (polaris) GPU 0 RPM mode Linux 5.11?"
date: 2021-08-17
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2021-08-17
looks like this feature is new with the 5.11 kernel i just updated to
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Fixes-Up-Polaris-2020](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Fixes-Up-Polaris-2020)
the lack of 0 RPM mode has been ideal for me since my cooling solution does not support it and it being on causes one fan to be 0% and the other to be 100%

does anyone know a parameter to disable 0 RPM mode?

i am already using the amdgpu.ppfeaturemask=0xffffffff parameter

edit: found out how to disable it in the vBIOS of the card
[https://www.overclock.net/conversations/disable-0-rpm-mode-in-rx-580-vbios.6778297/#convMessage-6804261](https://www.overclock.net/conversations/disable-0-rpm-mode-in-rx-580-vbios.6778297/#convMessage-6804261)

---

