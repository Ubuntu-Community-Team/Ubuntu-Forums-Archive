---
title: "Switching from lightdm causes taskbars to disappear"
date: 2018-02-26
forum: General Help
---

### Post by francisco333 on 2018-02-26
I have kubuntu 16.04, running unity (I don't remember why it runs unity by default instead of kde), but I recently installed a bunch of other desktop environments. However, the menu for the default login session disappears off the screen since there are so many options. Thus, I switched from lightdm to gdm, but when I logged in, the unity taskbars were gone, and even when I reset the desktop, the icons and power options on the top right were still not showing. Every time I restarted the computer the taskbars would disappear again. The same thing happened when I switched to lxdm and sddm. Only lightdm works correctly, but again, the menu disappears off the screen, preventing me from selecting some options. How do I get the other login sessions to work correctly with unity?

---

### Post by deadflowr on 2018-02-26
Switch from the unity-greeter to lightdm-gtk-greeter
Install the lightdm-gtk-greeter
```
sudo apt install lightdm-gtk-greeter
```
then set it as the greeter-session

Make a custom lightdm.conf file and add
```
SeatDefaults]
greeter-session=lightdm-gtk-greeter
```
restarting lightdm should now show the lightdm-gtk-greeter instead of the unity-greeter.
The ligthdm-gtk-greeter shows the desktop session options in a dropdown from the panel.
Unlike the unity-greeter which shows it in the username/password box.

More here:[https://wiki.ubuntu.com/LightDM]("https://wiki.ubuntu.com/LightDM")

---

