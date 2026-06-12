---
title: "Mouse position mismatch after browser unminimize, related with CompizConfig, 14.04"
date: 2014-04-23
forum: General Help
---

### Post by radddi on 2014-04-23
Minimizing a browser window and then unminimizing it causes the browser's perceived mouse position to be mismatched with the actual mouse cursor. Selected links, text, etc are about 20 pixels lower than where the mouse currently is. (screenshot) The problem is fixed when the window is maximized via keyboard shortcut. This applies to both Opera 12.16 and Firefox 28.

After testing I found that the problem is related to an unrelated fix for "Show Desktop" not working either via the launcher button, sticky corners or a keyboard shortcut -- unchecking the CopmpizConfig option Ubuntu Unity Plugin > Switcher > Show live previews of windows in the Switcher. When the option is checked the mouse mismatch doesn't occur but Show Desktop is broken. When the option is checked, show desktop works as intended but the above problem occurs.

Has anyone else had this problem?

Linux Lenovo-B570 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
CPU: Intel® Pentium(R) CPU B940 @ 2.00GHz × 2 
GPU: Intel® Sandybridge Mobile (HD 3000)

Thread about the Unity Show Desktop Bug:
[http://askubuntu.com/questions/419205/show-desktop-with-hot-corners-not-working](http://askubuntu.com/questions/419205/show-desktop-with-hot-corners-not-working)

---

### Post by strannik-dj on 2014-04-30
Yes, I am

---

### Post by auro2 on 2014-05-04
Hello!

I have been facing this issue myself too... But I found a fix recently. Made a quick video to fix it. :)
[https://www.youtube.com/watch?v=VFpt5rd1DJQ](https://www.youtube.com/watch?v=VFpt5rd1DJQ)

Hope this helps. :)

---

