---
title: "XServer won't start"
date: 2007-01-29
forum: General Help
---

### Post by Emanuel on 2007-01-29
Hey People,

I use Ubuntu 6.10

Everything was working fine, until I wanted to play a game so I decided to manually install new NVIDIA drivers.

After I installed them I also installed XGL/Compiz (NVIDIA).

== For the above stuff, i followed the steps at:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28Nvidia.29)

The problem is, when I now reboot, then the X Server won't start, it gave an error.
So I decided to uninstall XGL, and now when I reboot it says: XServer not available, please recondigure GDM properly, or something.

Also GDM START, won't start the X Server.

The only way for me to start the X Server is by typing logging in using the Text login screen, and then by typing: start x

How do I fix it , so that i will simply get the Graphical login screen again when rebooting the computer?

Thank you very much... I don't want to re-install Ubuntu...

---

### Post by Emanuel on 2007-01-29
After editing the gdm .conf file, X Server stats again.

But it doesnt show the original gdm welcome screen, instead it says:

No server has been configured and xdgdcm (or something) is not enabled.

Any ideas? Greetings.

---

### Post by Emanuel on 2007-01-29
It's fixed. Reinstalled GDM, Greetings.

---

