---
title: "oops - no desktop .... Kubuntu 6.10 -- Help"
date: 2007-02-27
forum: General Help
---

### Post by HW_Hack on 2007-02-27
I decided to move from Ubuntu 6.06 to Kubuntu 6.10 on my Dell B-130 laptop -- all went well - even got the Braodcom wireless working - many re-boots no problems. Last thing I did was run adept I installed wireless sniffer package   AND   a set of utils for DELL Latittude and Inspiron notebooks


Now 2 things are happening ---- It boots to a standard console login .... no KDE desktop 

Whe I do a forced shutdown is seems to hang on the last fw steps 

what error log should I look at --- and how do I get my desktop back 

Signed ---- stuck at the terminal prompt (I am able to login -- and I do know my way around a bit in the file system and can run vi just fine

---

### Post by erkki70 on 2007-02-27
hi,
Can you login to your session manager from console?
```
sudo gdm start
``` or ```
sudo kdm start
```Also you can:
```
sudo dpkg-reconfigure gdm
``` or ```
sudo dpkg-reconfigure kdm
```and edit your /etc/X11/default-display-manager to select wether you want gdm or kdm.
Hope it helps...

---

