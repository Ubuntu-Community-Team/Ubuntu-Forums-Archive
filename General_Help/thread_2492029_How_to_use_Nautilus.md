---
title: "How to use Nautilus"
date: 2023-10-28
forum: General Help
---

### Post by janvi2 on 2023-10-28
I have 2 Ubuntu systems with Nautilus, obviously diffrent versions. One is 22.04, the other is 18.04 LTS. The screendums below shows the appaerance of Nautilus on both systems

 22.04 shows a window in left coloumn with access possibilities to USB sticks or network drives while the 18.04 Nautilus shows nothing else than /home directory. I did not find any possibiltiy to enter file path manually or to show the version info of Nautilus itself. 
  If I use context menu „copy to“ or „move to“, a full feature window opens where it is possible to navigate all drives. They are mount proper and work successfull but I cannot navigate for reading purposes in the limited Nautilus window.           How its possible to force Nautilus always showing the extended window for navigation ?

---

### Post by ajgreeny on 2023-10-28
I gave up on gnome when gnome 2 was superceded by gnome 3 as I found all aspects of the new GUI unusable.
My feeling is that it has gone from bad to worse and I havent even looked at it for a long time.

However, I suspect there is a menu system for nautilus that you get to from a hamburger icon somewhere in the nautilus window. Fro that you may be able to ensure that the side pane of the window shows as default.

---

### Post by dragonfly41 on 2023-10-28
Searching finds this advice ...

[https://askubuntu.com/questions/861333/how-to-open-nautilus-file-manager-preferences](https://askubuntu.com/questions/861333/how-to-open-nautilus-file-manager-preferences)

For Preferences click on **Files**


Quote: &#8220;On Ubuntu 17.10.1, the top left corner of the screen next to Activities, you'll find 
Files
with a drop-down arrow:&#8221;
[URL="https://apps.gnome.org/en-GB/Nautilus/"]

https://apps.gnome.org/en-GB/Nautilus/[/URL]
[https://help.gnome.org/users/gnome-help/stable/files.html](https://help.gnome.org/users/gnome-help/stable/files.html)

P.S. you might try Thunar.  Personally I use Krusader.
And there are Nautilus Python extensions.

---

### Post by janvi2 on 2023-10-28
Thats it: Desktop - Activities - Files - Sidebar
After a tick, the missed features are back in Nautilus
Many thanks

---

### Post by MAFoElffen on 2023-10-29
> **ajgreeny said:**
> I gave up on gnome when gnome 2 was superceded by gnome 3 as I found all aspects of the new GUI unusable.
My feeling is that it has gone from bad to worse and I havent even looked at it for a long time.

However, I suspect there is a menu system for nautilus that you get to from a hamburger icon somewhere in the nautilus window. Fro that you may be able to ensure that the side pane of the window shows as default.
Nemo was a fork from Nautilus. Nautilus is now known as Gnome Files.

Nemo still has all the menus, preference tweaks, and theming kinds of things that they removed from Gnome Files. Nemo is the default for Cinnamon.

---

### Post by vanadium on 2023-10-29
Hit F9 to show/hide that side panel. In the latest GTK4 versions of nautilus (now shipping with Ubuntu 11.10), the side pane cannot be hidden, however will disappear when the Nautilus window is made smaller.

---

