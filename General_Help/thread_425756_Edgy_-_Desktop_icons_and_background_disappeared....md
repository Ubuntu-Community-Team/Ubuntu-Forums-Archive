---
title: "Edgy - Desktop icons and background disappeared..."
date: 2007-04-27
forum: General Help
---

### Post by 303 on 2007-04-27
along with the right-click context menu...
any ideas?

the "Desktop" folder still has all my folders and things in it but alas... nothing on the desktop
can't find anything about it anywhere

---

### Post by Pox on 2007-04-27
I'm assuming you're in standard GNOME ubuntu, so try ALT+F2 and running "nautilus &".

---

### Post by 303 on 2007-04-28
wow. that worked!!
Thank you very much!
I don't know what caused that to happen in the first place?

just curious, but could you elaborate a little on what that command was?
thanks again

---

### Post by mastahoratio on 2007-04-28
wow. i had the exact same problem just now. thanks!

---

### Post by Pox on 2007-04-28
> **303 said:**
> wow. that worked!!
Thank you very much!
I don't know what caused that to happen in the first place?

just curious, but could you elaborate a little on what that command was?
thanks again

Nautilus is the GNOME file manager - what you see when you are browsing your files.  However, it also manages the desktop.  I don't use GNOME, so I'm not sure why it wasn't there, but it could have crashed for some reason.

---

### Post by 303 on 2007-04-29
Well, it happened again for some reason, and I really screwed myself for this user profile..

Earlier I tried changing the menu icon for snazziness and all and now my panels are gone as well.
SO, that means:
1. No right click. Anywhere.
2. Can't run "run program" shortcut or pull up a terminal to fix it.

So I guess now I have to delete all those .gnome and pref files?
Unless you know how to fix from command line...

Edit: 
FIXED.
I just moved the folder with the custom menu icon to a different profile and logged back into the "broken" one and everything is back to normal. 
Now I'm unchecking "use custom icon" in the config. manager for the menu icon setting. I followed the guide for installing the new icon background step by step, don't know what went wrong there!

---

