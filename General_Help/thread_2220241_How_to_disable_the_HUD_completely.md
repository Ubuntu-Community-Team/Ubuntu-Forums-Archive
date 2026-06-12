---
title: "How to disable the HUD completely"
date: 2014-04-27
forum: General Help
---

### Post by bovender on 2014-04-27
I am having trouble disabling the HUD completely.

Since I use the ALT key a lot, it's cumbersome to have the HUD menu appear every time I press it, especially when running a virtual Windows box and pressing ALT+TAB to switch applications.

However, all attempts to unset the ALT shortcut for the HUD have failed so far.

I tried to unset the shortcut or set it to a different combination (ALT+SHIFT+F12 in my case) in Ubuntu's keyboard settings applet, and also disabled the shortcut in CompizConfig Settings Manager (CCSM).

Every time I reboot the laptop, the shortcut is reset to ALT.

What to do?

---

### Post by MrSteve on 2014-04-27
suggestion
try opening the system settings via sudo
in a terminal write
sudo gnome-control-center

then use the system settings > keyboard > shortcuts
and change the shortcuts from here ...

---

### Post by bovender on 2014-04-30
Well unfortunately, this did not work. HUD came back again.

---

### Post by deadflowr on 2014-04-30
I don't know if this works on Trusty, but if you have ccsm(compizconfig-settings-manager)
You can try going to the unity plugin and in that should be a setting for the HUD.
It should be listed as alt, but if you click on the button it will give options to change and a way to disable.
(uncheck enable)

Again, don't know if this works on Trusty.
(I'm on Precise ATM)

---

