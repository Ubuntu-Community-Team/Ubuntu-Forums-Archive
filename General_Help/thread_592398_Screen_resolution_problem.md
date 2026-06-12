---
title: "Screen resolution problem"
date: 2007-10-26
forum: General Help
---

### Post by childresspta on 2007-10-26
I seem to have the opposite problem as everyone else.  My resolution is fine during login, but after I login it goes to 800x600.  1024x768 is an option, but when I select it in the settings the desktop does not fit the screen, the toolbar and icons go off screen.  The last thing I was doing was trying to install codecs for kaffine and nothing happened while I was working with it, but the next day when I booted up it did it.  Any help?

---

### Post by jenhsun on 2007-10-26
1. After login, check your system/Administration/Restricted Driver Manager, do you have any restricted driver? If does, which kind? ATI or Nvidia?
You can enable it and install the driver. Look it can solve the problem or not. If don't, continue to the next...

2. In your System/Preference/Hardware Information, what graphic card do you use?
write it down.
3. Go to get your monitor information. You need Vertical and Horizontal Hz range.
4. Open your terminal, type
sudo dpkb-reconfigure xserver-xorg
and follow all manual setup. Then reboot to see what you got.

---

### Post by childresspta on 2007-10-26
Sorry, I forgot to mention I am running kubuntu feisty, so I don't have the restricted drivers manager, but yes I have installed the drivers and enabled.

---

### Post by jenhsun on 2007-10-26
> **childresspta said:**
> Sorry, I forgot to mention I am running kubuntu feisty, so I don't have the restricted drivers manager, but yes I have installed the drivers and enabled.

Good, continue to all my steps and see what's going on.

---

