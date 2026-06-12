---
title: "Unable to install stuff"
date: 2007-06-29
forum: General Help
---

### Post by ev5unleash1 on 2007-06-29
[FONT="Comic Sans MS"]Hi,

I've had Ubuntu for while now and I loved it. But when I tried installing the Opera Browser .deb file. Once I downloaded it and tried installing it. I got this message

Only one software managment software is allowed at once
Please close all other applications.
(Listing some other applications that I made sure was closed even though System Monitor)

I also closed all other applications exsept the installer it's self. Now even when I try to update is gives me this message.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Now i can't even install or uninstall anything.

PLEASE HELP ME!!![/FONT]

---

### Post by mikewhatever on 2007-06-29
Just do what it says. Open Applications>Accessories>Terminal and type
> sudo dpkg --configure -a

---

