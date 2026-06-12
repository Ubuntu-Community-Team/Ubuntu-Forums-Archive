---
title: "Cursor disappears after suspending and then logging back in Lubuntu"
date: 2016-08-24
forum: General Help
---

### Post by johnbross on 2016-08-24
My cursor disappears after suspending and then logging back in Lubuntu (LTS, latest version)

  
I don't know why this happens, I tried default settings for the cursor, different theme, ... but with no result.

---

### Post by PaulW2U on 2016-08-24
> **johnbross said:**
> My cursor disappears after suspending and then logging back in Lubuntu (LTS, latest version)

  
I don't know why this happens, I tried default settings for the cursor, different theme, ... but with no result.
Presumably you have Intel graphics?

If so then it's bug [#1568604]("https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/1568604") which should see a fix soon. The work around for now is: ```
Ctrl+Alt+F1
Ctrl+Alt+F7
```
which should restore the mouse pointer until you suspend and resume again. If your graphics are not Intel then please let us know.

---

### Post by johnbross on 2016-08-24
> **PaulW2U said:**
> Presumably you have Intel graphics?

Correct. Thanks for the temporary solution.

---

