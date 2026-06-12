---
title: "Unity 3D windows not snapping"
date: 2013-06-01
forum: General Help
---

### Post by mortrca on 2013-06-01
After restarting my computer (running 12.04), the windows no longer "snap" to half of the screen or to full screen when I drag them to the edges. ```
/usr/lib/nux/unity_support_test -p
``` reports no errors. I have attempted to get it working by restarting the computer again, but there was no change in behavior.

---

### Post by vanadium on 2013-06-01
Firt, you may try to check the settings in Compiz-config settings manager. The "Grid" plugin is responsible for this function. If that does not work, you may try to reset compiz: see [http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html](http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html)

---

### Post by ksanger on 2013-06-19
Awesome thank you.  Using Compiz-config settings manager to uncheck grid eliminates the window filling up the display when you drag it to the top.  I was looking for a way to turn that off.  I prefer clicking the window full screen icon and never understood why we needed another annoying method that I didn't want.  Sellecting full screen is much nicer than having the computer think I want full screen when really I just want a tall window so I can see the bottom of the page.

Thanks again.  :)

---

### Post by mortrca on 2013-06-19
Sorry about not getting back about this. I don't know what happened, but the issue went away without further work on my part.

---

