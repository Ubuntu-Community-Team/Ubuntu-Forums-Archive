---
title: "How can I edit the notification area?"
date: 2008-04-09
forum: General Help
---

### Post by geokker on 2008-04-09
There's 7 icons and the clock which takes up precious space on the panel. I want to remove the redundant network icon and glipper. How can I do this?

---

### Post by TeoBigusGeekus on 2008-04-09
Just right click them and select Remove from panel.

---

### Post by geokker on 2008-04-09
On the right-click context menus I only have 'enable networking', about and prefs (Glipper). No, there's nothing in prefs either.

---

### Post by TeoBigusGeekus on 2008-04-09
I'm on a winxp machine right now, so I can't really test it, but have you tried dragging and dropping them on Desktop and then deleting them from there?
If that doesn't work, delete your whole panel and add a new one with only the things you want.

---

### Post by geokker on 2008-04-09
I'm taking about the 'notification area' item which can be added to the gnome-panel via right-click> add item. It is akin to the Windows system tray. I cannot seem to hide/remove many items that appear in this area notably the ugly, large and redundant (for me) Glipper and network icons.

So I wonder if there's a notification area config file or a gnome-panel general config.

---

### Post by TeoBigusGeekus on 2008-04-09
Sorry, I didn't understand...:oops:

---

### Post by ryanhaigh on 2008-04-09
For the network manager you can disable the applet starting through system>preferences>sessions and uncheck the box for network manager. This shouldn't have much effect if your using a wired network or have a manually configured wireless.

As for glipper I have no idea whether it can be removed from the tray as the tray icon actually provides functionality (although if you remember ctrl-alt-c that functionality is easily replaced). Perhaps there are other clipboard managers available that would better suit your needs.

---

### Post by eln0k0fl on 2008-05-29
I also have the same issue as ryanhaigh. The network manager tray applet can't be removed. My  network manager is not checked in the system-preferences-sessions tool and it still shows up in the tray. Right clicking on it only allows you to enable/disable networking, and configure the wireless networks. I use a single wired network with fixed addresses and NO wireless. I don't want to delete the entire panel to get rid of one applet because this panel has a lot of things that I need such as menus in it.

---

### Post by ryanhaigh on 2008-05-29
You can kill the applet by openning the run dialog (alt-f2) or a terminal (accessories>terminal) and issuing the command killall nm-applet

It seems strange that it is starting even though you have disabled the entry in Sys>Prefs>Sessions. Have you perhaps used the remember current processes (not sure exactly what its called but its in that same dialog).

---

