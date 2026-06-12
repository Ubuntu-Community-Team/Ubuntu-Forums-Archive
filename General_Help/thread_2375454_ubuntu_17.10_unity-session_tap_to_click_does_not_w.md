---
title: "ubuntu 17.10 unity-session tap to click does not work"
date: 2017-10-24
forum: General Help
---

### Post by monkeybrain20122 on 2017-10-24
As the title says, tap to click works in gnome but not in unity-session in Artful. There is no "tab to click" option in System Settings > Mouse & Touchpad in Unity-session like in Xenial.

---

### Post by mc4man on 2017-10-24
A unity session would need xserver-xorg-input-synaptics installed for this & to get fuller options in System Settings > Mouse & Touchpad
(could interfere with a ubuntu or gnome sessions's use of libinput
Note: the xserver libinput package is needed so never remove it..

---

### Post by monkeybrain20122 on 2017-10-24
> **mc4man said:**
> A unity session would need xserver-xorg-input-synaptics installed for this & to get fuller options in System Settings > Mouse & Touchpad
(could interfere with a ubuntu or gnome sessions's use of libinput
Note: the xserver libinput package is needed so never remove it..

Hi, installing xserver-xorg-input-synaptics works. I haven't found any adverse effect on the gnome sessions. In fact as a bonus a script I used for enabling both edge and two finger scrolling works now in both Unity and gnome sessions (lininput only allows two finger scrolling, the edge option in gnome's settings never works)

Thanks.

---

### Post by bimmelbommel on 2017-12-03
> **monkeybrain20122 said:**
> Hi, installing xserver-xorg-input-synaptics works. I haven't found any adverse effect on the gnome sessions. In fact as a bonus a script I used for enabling both edge and two finger scrolling works now in both Unity and gnome sessions (lininput only allows two finger scrolling, the edge option in gnome's settings never works)

Thanks.

libinput is supposed to replace synaptics so reinstalling synaptics kind of defeats this purpose ;)

Here is a different solution:
Go to /usr/share/X11/xorg.conf.d and look for a file called XY-libinput.conf with XY being a number, e.g. 40-libinput.conf

Look for the part that says:

```
Section "InputClass"
        Identifier "libinput **touchpad** catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "libinput"
EndSection
``` 

Here you can add options like "Tapping" (click on tap) or "NaturalScrolling" that you would have had in the GUI before with the synaptics driver.


```
Section "InputClass"
        Identifier "libinput touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "libinput"
        **Option "Tapping" "True"**
        **Option "NaturalScrolling" "True"**
EndSection
``` 

If "Driver" says synaptics, change it back to libinput.

Reboot (or log out and log in again) and you should be good to go.

---

### Post by mc4man on 2017-12-03
> **bimmelbommel said:**
> libinput is supposed to replace synaptics so reinstalling synaptics kind of defeats this purpose ;)

Here is a different solution:
Go to /usr/share/X11/xorg.conf.d and look for a file called XY-libinput.conf with XY being a number, e.g. 40-libinput.conf


And not having gui settings defeats the purpose of being user friendly..

---

