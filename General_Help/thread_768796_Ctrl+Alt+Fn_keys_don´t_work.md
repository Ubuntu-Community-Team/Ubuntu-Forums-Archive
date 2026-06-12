---
title: "Ctrl+Alt+Fn keys don´t work"
date: 2008-04-26
forum: General Help
---

### Post by pedor on 2008-04-26
I have upgraded to hardy and try to install the ati driver with envy which doesn´t work. I have now removed the ati driver and envy.
Now I can´ t switch to terminal mode when I am in X .
what has changed?   :confused:

---

### Post by ryanhaigh on 2008-04-27
Is there something like Option "DontVTSwitch" in /etc/X11/xorg.conf? This disables switching to virtual terminals. From my own experience the ati driver has issues with this so envy may have disabled it by using that option.

---

