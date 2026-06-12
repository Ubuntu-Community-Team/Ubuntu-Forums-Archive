---
title: "[SOLVED] X org"
date: 2008-04-21
forum: General Help
---

### Post by f37u5g0d on 2008-04-21
I am pretty sure I deleted the xorg file or some file that is critical to my computer's hardware configuration when I was "cleaning" my /home folder.  Now when I tell my computer to use my ATI (9550) fglrx driver (restricted driver) and I reboot I get an error that says ubuntu has to run in low graphics mode.  If I configure and tell it to use the driver again the same thing happens.  If I do boot all the way the restricted drivers windows says that the driver is in use but the box is not checked.
Also whenever I boot I get an error that says this:

"The X system keyboard settings differ from your current GNOME keyboard settings.

Expected was model "pc101", layout "us" and no options, but the the following settings were found: model "pc105", layout "us" and no options.

Which set would you like to use?"

The options are x session and gnome.  It doesn't matter which I choose either way the keyboard works but it gives the same message every time I boot no matter which I choose.  Help!

---

### Post by Thanoulis on 2008-04-21
You need to edit your xorg.conf file:
```
sudo gedit /etc/X11/xorg.conf
```
Under Section InputDevice with Identified Keyboard, change the *Option "XkbModel" "pc101"* with *Option "XkbModel" "pc105"*. Then restart your X session. :)

---

### Post by f37u5g0d on 2008-04-21
I figuered out that I had to run sudo dpgk-reconfigure xserver-xorg and that fixed my ATI card/driver problem but now the keyboard is often funky.  Often when a box pops up that wants my password (firefox master, or system admin password) I have to press the alt button before I can type.  Also if I open a nautilus  window clicking on anything moves the windows around as if I am holding alt key.  It seems like the alt key is being pressed on it's own.  If I press alt then the mouse and keyboard are normal again.  Help!  Also if I set compiz effects to extra or custom they return to normal again as soon as I close and re-open that window.  Why is this happening?

---

### Post by f37u5g0d on 2008-04-21
If I open a nautilus window.  Click on the desktop and then click back on that window I get this mysterious alt behaviour.  As if I am holding down the alt key even though I am not.  Scrolling makes the window go transparent and clicking grabs the window to move it.

---

### Post by prshah on 2008-04-21
> **f37u5g0d said:**
> If I open a nautilus window.  Click on the desktop and then click back on that window I get this mysterious alt behaviour.  As if I am holding down the alt key even though I am not.  Scrolling makes the window go transparent and clicking grabs the window to move it.

Maybe you have accidentally turned on keyboard accessibility technologies? Click on System-Preferences-Universal Access-Keyboard Accessibility, then uncheck "Enable Keyboard Accessibility features".

If it is already unchecked, check it, OK/Close, then go back and uncheck it, OK/Close.. did it help?

---

### Post by f37u5g0d on 2008-04-21
This is embarrassing.  I accidentally applied the incorrect keyboard type in dpkg-reconfigure xserver-xorg.  (I put 105 instead of 104).  Nevermind all of the trouble!  Again super embarrassing but at least I'm learning.  (Ubuntu is awesome).

---

