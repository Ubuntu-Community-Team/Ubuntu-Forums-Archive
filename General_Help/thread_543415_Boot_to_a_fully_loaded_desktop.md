---
title: "Boot to a fully loaded desktop"
date: 2007-09-05
forum: General Help
---

### Post by treis on 2007-09-05
Ubuntu is still loading some things after it shows the desktop resulting in a "working" mouse icon.  Is there a way to get it to hold off on showing the desktop until the system is fully loaded and ready to use?

---

### Post by Shoot3r101 on 2007-09-05
Hmmm. This sounds more like a "add-on" request other than a fix. I don't know what to say... But why does this bother you?

---

### Post by treis on 2007-09-05
I don't know, it just bugs me.  I realize it's a cosmetic thing but I think it should have a pretty easy fix.  Just a matter of changing the boot order to having the desktop showing the very last thing.

---

### Post by fragos on 2007-09-05
Gnome and the desktop must start before the applications are loaded.  In System-> Preferences-> Sessions-> Session Options Tab you can uncheck "Automatically Save Changes to Session".  That way the applications you're running at shutdown won't be restarted.  If you want some apps started at boot don't uncheck that parameter and leave those apps in the 2nd workspace and you may not have to watch them start.

---

