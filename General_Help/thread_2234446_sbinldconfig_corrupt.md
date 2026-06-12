---
title: "/sbin/ldconfig corrupt"
date: 2014-07-14
forum: General Help
---

### Post by Wurstinator on 2014-07-14
Hello,
about an hour ago, my Ubuntu 12.04 64bit randomly froze so I had to restart (with a hard reset). After that my screen stays black after the "ubuntu" loading screen (basically where the login screen should be).
This appears to be an issue with the graphics driver (I have an Nvidia installed) since pressing the power button causes a "soft reset" i.e. a normal shutdown, like it usually would.
However, I already removed my nvidia drivers and reinstalled most of them in recovery mode so there seems to be more to it. Also, Windows on this same computer works just fine so it's not a hardware defect.
The weirdest issue I have found so far lies within /sbin/ldconfig. Calling /sbin/ldconfig -v will basically destroy the shell, by swapping around the ASCII characters so nothing is readable anymore. That also caused many errors when removing packages for example, saying that [lots of unreadable characters] is not a known library type.
I would be grateful for help so I don't have to reinstall Ubuntu as a whole.

---

