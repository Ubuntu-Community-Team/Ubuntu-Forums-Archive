---
title: "Default Panel settings"
date: 2007-10-12
forum: General Help
---

### Post by BlueScotch on 2007-10-12
Is there anyway to restore the settings/icons that are installed by default on the top panel of an Ubuntu installation?

Somehow I keep on accidently deleting/removing parts from the top menu, the two "applications", i suppose the word would be, I cannot find to re add are the network applet (the one that allows me to select wireless network versus wired connection from a drop down menu) and the default battery monitor.

If I am not explaining my problem as well as I can, I will try to explicate a bit more.

Thanks.

---

### Post by picopir8 on 2007-10-12
The network application is "NetworkManager"
The battery icon is "Gnome Power Manager"

Try removing the packages then reinstalling them.

However, I would first try booting to a command line, and try moving your ~/.gnome directory to something like ~/.gnome_bak and then reboot.  If it does not see the customization folder, it might recreate it with default settings.  If it does not work then can just rename it again to get back what you had and then try removing and installing the packages.

---

