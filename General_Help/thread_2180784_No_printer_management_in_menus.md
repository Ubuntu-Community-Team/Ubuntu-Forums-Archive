---
title: "No printer management in menus"
date: 2013-10-14
forum: General Help
---

### Post by 4dummies on 2013-10-14
I just installed xubuntu 13.04 AMD, and got my HP printer enabled.  Hooray.

But I'm used to having a printer management thing available in the menus, probably a CUPS thing.  I don't see one, and I'm not even sure if one is installed.

---

### Post by ajgreeny on 2013-10-14
Install hplip-gui if you don't already have it and that will give you a wonderful printer management application to use from the system-tray.

---

### Post by 4dummies on 2013-10-14
Okay, I installed it.  I don't see anything in the menus, or in that little dock at the bottom of the screen.

Perhaps I don't understand what the system tray is.  Or perhaps it does not exist in Xubuntu.

While I'm at it, I was pretty sure there was a "Main Menu" menu manager in the menus, but I can't find that either.

---

### Post by ajgreeny on 2013-10-14
It certainly works OK in Xubuntu 12.04 (with xfce 4.10); I've not tried 13.04, but would imagine it still works in that as well.

Have a look in the xfce4 settings manager ->Session & Startup tab.  There should now be an entry for HP-Toolbox (or similar) with the command hp-systray.  I think it should start when you next boot or login to a new session.  If not you may need to add it to the startup list manually, and you may even need to make a compound command ```
bash -c "sleep 10; hp-systray"
``` that slows the apps start by a few seconds, as I did to avoid the error message that hp-systray could not start.

For menu edits 12.04 uses alacarte and the item "Main menu"is in the menu's settings group near the top of the main menu.  You can also get to it by right clicking on the main menu button/icon, choosing Properties, then the "Edit Menu" button.

---

### Post by JKyleOKC on 2013-10-14
If your printer is installed through CUPS, you manage it through the web broser at [http://localhost:631](http://localhost:631) (which is simply a loopback link to your local machine at port 631, where CUPS listens for instructions). While I used hplip back in Win98 days, I've avoided it on Xubuntu simply because the first time I tried to use it, it conflicted with CUPS. It might work just fine for you however. It will probably be in the Applications->System menu...

---

### Post by ajgreeny on 2013-10-15
On my system, Xubuntu 12.04, the HPLIP Toolbox is in Accessories, not System.

---

