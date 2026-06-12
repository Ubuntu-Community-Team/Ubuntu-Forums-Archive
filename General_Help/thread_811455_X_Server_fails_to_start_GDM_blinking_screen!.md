---
title: "X Server fails to start GDM blinking screen!"
date: 2008-05-29
forum: General Help
---

### Post by Michelpt on 2008-05-29
Hello everybody,

Please need some help with xserver configuration on Ubuntu Feisty. 

I was navigating on net when rapidly Firefox was crashed and I could not run it again as well as konqueror or other kde application. 

Error was smth "could not run kde launcher" or so. I restarted Xserver by Ctrl-Alt-Backspace and till today see [COLOR="Red"]blinking gdm screen[/COLOR], so I can't login to X, however I can login to console (Ctrl - Alt -F1). 

I see that **gdmgreater** occupies some cpu time (10%-50%) due to blinking screen. 

- I tried to reconfigure xserver by **dpkg-reconfigure-xserver-xorg**, 
- I installed proprietary drivers (Via Technologies), 
- after has no luck with actions above, kernel was recompiled with via graphics chipset support, but still have the same problem;
- then I upgraded system to Ubuntu Hardy 8.04 and problem persists;

even still had not luck even if I put "vesa" driver in my xorg.xonf. 

When I try to run X manually, I can see this in logs: 
> Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May 29 10:53:41 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module already built-in
(EE) AIGLX: Screen 0 is not DRI capable
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.


I tried to disable "dri" module in xorg.conf but also had not luck. 

Please Help and thanks in advance!

---

