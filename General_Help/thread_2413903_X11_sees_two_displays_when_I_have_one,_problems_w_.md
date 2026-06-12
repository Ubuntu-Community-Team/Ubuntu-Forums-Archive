---
title: "X11 sees two displays when I have one, problems w/ GLX &amp; swrast"
date: 2019-03-03
forum: General Help
---

### Post by Peter_Brandon on 2019-03-03
I have one monitor, but $DISPLAY equal :1, and /tmp/.X11-unix shows unix sockets for X0 and X1.  I did at one time have a different monitor on this computer and there are graphics processors both on the Intel chip and separately.  I'm not sure, but suspect that the display connecting to X1 is causing a couple problems:

I've tried to install LXD with gui access using the instructions at: [https://blog.simos.info/how-to-easily-run-graphics-accelerated-gui-apps-in-lxd-containers-on-your-ubuntu-desktop/](https://blog.simos.info/how-to-easily-run-graphics-accelerated-gui-apps-in-lxd-containers-on-your-ubuntu-desktop/) .  Tried both LXD from snap and from apt.  When I test it's 3D GUI in either, I get this:

[FONT=monospace][COLOR=#000000]$ glxgears[/COLOR]
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
X Error of failed request:  BadValue (integer parameter out of range for operation)

I modified the LXD profile so it would use X1 (not sure I got that 100% right), but get the same error.

I've also tried to run Steam, but get the same libGL errors above.  It can't load swrast (though it's on my Ubuntu OS), and says it cant find matching fbConfigs or visuals (whatever those are).

To fix the double display sockets problem, I tried to create an xorg.conf.  I tried X -configure both to a non-existent display (:2) and from the root prompt in system recovery.  Run either way, I get a segmentation fault.  Something seems to be badly wrong w/ my X11 configuration.

Any thoughts?

[/FONT]

---

