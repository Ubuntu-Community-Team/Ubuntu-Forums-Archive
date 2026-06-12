---
title: "Lubuntu system tray popup menus disappear"
date: 2019-12-18
forum: General Help
---

### Post by tmichaelmcn on 2019-12-18
I have installed Lubuntu 18.04 on a Toshiba c855 laptop.  The popup menus in the system tray disappear as soon as I move the mouse pointer onto them, making it virtually impossible to use apps like clipit or the network manager.  I had this same problem on an old IBM Thinkpad.  Any suggestions would be greatly appreciated.

---

### Post by mörgæs on 2019-12-19
Lubuntu 18.04 runs the abandoned LXDE desktop environment. From 18.10 onwards LXQT took its place.

18.04 can be used "as is" but don't expect support from developers. Better to do a clean install of 19.10.

---

### Post by guiverc on 2019-12-19
My guess is you're using a hidden panel - if you prevent your panel from hiding, the issue will be gone. 
Can you please confirm you've set your panel to be hidden.

[I]I'm currently using Lubuntu 20.04, however I've written about this issue before (on 18.04) so I'll look up whatever it's reminding me of, but I'm sure it's related to the hidden panel/

Added:  I could have been thinking of [/I][https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/1611264](https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/1611264) or [https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/1804899](https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/1804899) ;* if you want you can have a look and see if it describes your issue (click affects-me to maybe).  If it is that, not having the panel hide is the easiest fix.  If however you're talking about something else - please elaborate. *

---

