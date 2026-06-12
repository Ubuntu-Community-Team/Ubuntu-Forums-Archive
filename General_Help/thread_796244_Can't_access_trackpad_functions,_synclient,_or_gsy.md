---
title: "Can't access trackpad functions, synclient, or gsynaptics"
date: 2008-05-16
forum: General Help
---

### Post by Jonolith on 2008-05-16
I just installed xubuntu 8.04 on my iBook G3 500mhz, and I finally have everything working except I can't seem to access the trackpad functions.  I've gone through a bunch of different threads to try to fix it, and I've spent a lot of time tinkering with my xorg.conf, but no matter what I do, gsynaptics and synclient both say that my SHMConfig is not on.  I've tried using both Option "SHMConfig" "on" and Option "SHMConfig" "true" and neither works.  If I add options to try to enable scrolling or corner taps directly to the xorg.conf file, it doesn't seem to have any effect.  If I do sudo tpconfig -i, it does recognize the touchpad, and it's working fine for basic functionality, so I have no idea why I can't configure it.  Ideally, I'd like to be able run gsynaptics to configure the trackpad, but I'd be happy getting corner taps and edge scrolling to work with some other method.  Any help anyone could give me would be greatly appreciated.  Thanks!

---

