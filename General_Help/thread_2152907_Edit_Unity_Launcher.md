---
title: "Edit Unity Launcher"
date: 2013-06-09
forum: General Help
---

### Post by stepheny on 2013-06-09
What files do I need to edit to make changes to an application launcher in the Unity Launcher? For instance, to allow me to launch chromium-browser in incognito mode with a right click selection

---

### Post by stinkeye on 2013-06-09
Open gedit and drag the application from the dash(won't work from launcher) into the gedit window.
Then edit the .desktop file and use **File > Save As** to save to **~/.local/share/applications**
My chromium launcher has a right click incognito mode without editing.

May need to remove and readd your app to the launcher.
Removing the relevant .desktop file from **~/.local/share/applications** 
will revert to using the default launcher from /usr/share/applications.

---

### Post by 25tom on 2013-06-09
Ubuntu Tweak has the ability to edit Quicklists (which is what I believe the launcher right click menus are called). It does have the ability to powerfully edit hidden features, so use it carefully, but I've never had any problems from editing the Quicklists using it. You often have to logout/re-login for changes to take effect.

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Hope this helps :)

---

### Post by stepheny on 2013-06-09
Thanks to 25tom and stinkeye

---

