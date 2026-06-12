---
title: "Rebind &quot;virtual terminal(?)&quot; key?"
date: 2007-02-18
forum: General Help
---

### Post by Gibbs on 2007-02-18
Hey,

When you press CTRL-ALT-F1 you enter (what I think is called) one of the virtual shell terminal. For practice reasons I'm running Ubuntu inside of Ubuntu with VMWare Workstation. 

I want to know if I can rebind CTRL-ALT-F1 to something different so that I can access the virtual terminal. It isn't listed in Preferences > Keyboard Shortcuts. Also is there a terminal command to go to the "virtual" terminal?

Any help appreciated.

Thanks!

---

### Post by Franchie on 2007-02-21
These terminals are directly controlled by the X server you are using; i'm not sure what the situation is under a VM...

Take a look at your xorg.conf file (type: man xorg.conf), especially the following items in the Serverflags section:
Option "DontVTSwitch" "on/off"
Option "DontZap" "on/off"

Hope this helps,
F.

---

