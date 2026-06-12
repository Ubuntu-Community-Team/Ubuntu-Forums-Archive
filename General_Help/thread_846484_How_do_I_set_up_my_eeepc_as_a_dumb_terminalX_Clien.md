---
title: "How do I set up my eeepc as a dumb terminal/X Client?"
date: 2008-07-01
forum: General Help
---

### Post by KenBW2 on 2008-07-01
I have a network of 3 Ubuntu PCs:

```

kenneth-desktop              bill-desktop
   |_____________ROUTER_____________|
                   |
kenneth-laptop---WIFI AP

```

I'd like to set up my EeePC (kenneth-laptop) to be a dumb terminal/X Client for my Desktop (kenneth-desktop).
VNC isn't an option - the eeepc isn't powerful enough for it, but I've tried using XDMCP through the Options menu on the login screen. It brings up a window with kenneth-desktop.local and bill-desktop.local. Selecting either of these drops me back at the eeepc's login screen, or logged in session if I have one running.

I have attempted using the desktops to attempt connecting: the result is that kenneth-desktop can remotely connect to bill-desktop, but not the other way - this having the same result as the eeepc. I have made sure I have the X Server packages installed, although I'd appreciate confirmation that I have all of them.

If it's relevant these are my resolutions:
kenneth-desktop: CRT 1152x864
bill-desktop:    LCD 1024x768
kenneth-laptop:  LCD 800x480
Specs are in my signature

Thanks in advance :D

---

### Post by KenBW2 on 2008-07-01
*bump*

---

