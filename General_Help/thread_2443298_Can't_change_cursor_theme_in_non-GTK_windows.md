---
title: "Can't change cursor theme in non-GTK windows"
date: 2020-05-13
forum: General Help
---

### Post by littledj on 2020-05-13
I'm have issues changing my cursor from DMZ-Black to Oreo_Blue_Cursors. In GTK windows (Google Chrome, Firefox, etc.) the cursor works fine but when I go to non-GTK windows (The desktop, etc.) the cursor defaults to a low res DMZ-Black cursor. Even when using the built-in cursors like Yaru it still happens. I have tried just about everything from overwriting the DMZ-Black folder with my cursor to trying to move the cursor to the /usr/share/icons folder. I have looked through multiple threads about the same issue and none seem to fix the problem. When installing Ubuntu 20.04 I had issues loading the login screen and had to install lightdm, maybe that has something to do with it, but I don't know.

---

### Post by Dennis N on 2020-05-13
You may need to change the default cursor to your new theme. Follow these steps in _Getting Cursor to Work Everywhere_:

First, the cursor theme folder must be located in** /usr/share/icons**. Copy it there if necessary.
Then, we install the new cursor into what's called the alternatives system (used in Debian-based distros like Ubuntu):
```
sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/put-cursor-theme-name-here*/cursor.theme 20
```

Then we make the new cursor the default. Follow the instructions at the bottom of the output from this command to do that:
```
sudo update-alternatives --config x-cursor-theme
```
The new cursor should now appear everywhere. Reboot may be needed.

*this name appears on the cursor folder. For example, DMZ-White.

---

