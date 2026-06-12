---
title: "Panel icon for Dropbox loads and then disappears"
date: 2014-12-10
forum: General Help
---

### Post by winecurmudgeon2 on 2014-12-10
This seems completely unrelated to most of the missing Dropbox icon threads. None of the usual fixes have worked, and the icon was working yesterday. But when I turned on the computer this morning, the panel icon was gone. Dropbox is running, according to task manager. libappindicator1 is installed.

I have purged and reinstalled Nautilus-Dropbox. I have tried [this fix]("http://www.webupd8.org/2014/01/fix-dropbox-fails-to-start-with.html") and [this one]("http://www.elementarynow.com/quick-tip-restoring-dropbox-indicator/") without succes. The best I have been able to do is to get the panel icon to load on boot, but it disappears about the same time that the network manager icon loads in the panel. I disabled Dropbox on start and loaded it after I had an Internet connection, but this didn't seem to make any difference.

At one point, I got the following error message when starting Dropbox: "Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files." I think this was an icon issue, and fixed it.  In addition, though task manager says the .dropbox-dist file is running, that file has not always been in my home folder where it should be and I have had to restore it from the trash.

 My hunch, after some Googling, is that this might be a Nautilus problem. But purging and reinstalling Nautilus didn't help.

I'm running 64-bit Xubuntu 14.04. Any thoughts are much appreciated.

---

### Post by Paulgirardin on 2014-12-10
Can't help with dropbox - I dropped them when they started employing dodgey board members.
But,MEGA.com have a nice linux application and 50 free GB.Also Copy.com is an alternative.

---

### Post by Kurt_Alan on 2014-12-19
i pay dropbox.com almost $500.00 per year for two accounts.  I use them ONLY because of their powerful features such as "selective sync."  I have not found any other storage site with same.  To me this is a critical and indispensable function . . . 

Do you know of one?

---

### Post by vasa1 on 2014-12-20
Have you tried killing the panel in which the Dropbox icon is supposed to appear and then restarting the panel? I need to do that to get the icon to appear but this is with Lubuntu Openbox session and the tint2 panel.

---

