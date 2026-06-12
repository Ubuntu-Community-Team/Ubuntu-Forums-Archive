---
title: "Compiz effects slow after upgrade to Hardy"
date: 2008-05-07
forum: General Help
---

### Post by Damocles1 on 2008-05-07
Im aware there are a some similar posts but none of them helped me with this issue. Since i upgraded to Hardy, compiz desktop effects seem to run with significantly slower performance than they did on Gutsy (for example things like Rotate Desktop or Shift Switcher really cause low fps when more than 3 or 4 windows are open). This is **not** because of insufficient hardware, i'm running it on a Thinkpad Z61p (ATI MOBILITY FireGL V5200, using restricted driver.. and yes, it is enabled) and everything worked fine on Gutsy. However, i read several posts saying one should uninstall either xserver-xgl or compiz package (because they're supposed to be no longer required on Hardy) and enabling Desktop effects via System > Preferences > Appearance > Visual Effects. I tried that but somehow once I enable "Extra" desktop effects nothing changes and the option is reset to "None" when i reopen Visual Effects tab. Direct Rendering isnt the problem either, glxinfo said:
```
glxinfo | grep 'direct render
direct rendering: Yes

```
In addition to that, when xserver-xgl is not installed, desktop effects won't work even if compiz is installed. Is there maybe something i have to reconfigure by hand to make this work?

---

