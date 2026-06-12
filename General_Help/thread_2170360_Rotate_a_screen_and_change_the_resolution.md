---
title: "Rotate a screen and change the resolution"
date: 2013-08-25
forum: General Help
---

### Post by ODBWilson on 2013-08-25
I am able to change the resolution and rotate a screen in "Display" section on the desktop
And upon rebooting, it keeps the settings.
Just wondering where the settings are stored (which files).  I need it for my application.

And I tried to change the xorg.conf to rotate the screen or change resolution.  But unfortunately, there is no effect at all.
I am using Ivy Bridge 1037U with Intel HD 2500 on Mythbuntu 12.04 with XFCE4.
Any clues?


Thanks,
Wilson

---

### Post by Toz on 2013-08-26
> **ODBWilson said:**
> I am able to change the resolution and rotate a screen in "Display" section on the desktop
And upon rebooting, it keeps the settings.
Just wondering where the settings are stored (which files).  I need it for my application.
The settings are stored in $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml. $HOME is your home directory and .config is a hidden directory in your home directory. If you are using Thunar, you need to Ctrl+H to view hidden directories.

---

### Post by ODBWilson on 2013-09-02
Yup it works to change the displays.xml.
Anyone knows how to change the xorg.conf to rotate a screen with Intel ivy bridge?
P.S.  Nvidia works fine with:
Option "Rotate" "left"

---

### Post by The Cog on 2013-11-20
Can I just mention arandr please. It's a gui version of xrandr - not all the options, but most, and nice and easy to use.
I think the package is also called arandr.

---

