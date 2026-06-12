---
title: "Problem running program with WINE!!!"
date: 2008-05-14
forum: General Help
---

### Post by ryanconnarton on 2008-05-14
I installed Cakewalk SONAR 4 Home Studio to my distro of ubuntu studio and when I open it, it sometimes pops up (or starts to pop up) and then my cursor disappears where the Cakewalk SONAR 4 window is but the cursor displays on the ubuntu taskbar and everything but once I try to open this program it makes everything start to graphically screw up and it causes me to restart ubuntu studio. What am I doing wrong here with Wine? And I clicked Add/Remove from the main menu to uninstall Wine but yet it still appears with all of the windows programs in the ubuntu taskbar main menu? Any help would be greatly appreciated. Help is a wonderful thing.

---

### Post by Mr A Mouse on 2008-05-14
Hi, Ryan. Cakewalk SONAR 4 is not listed in the Wine apps database ([http://appdb.winehq.org/](http://appdb.winehq.org/)) as workable--indeed, it's not listed at all. Cakewalk Sonar 3 is listed as not working. 

If you want to uninstall Wine, try going through the Synaptic admin panel rather than Add/Remove.

---

### Post by ryanconnarton on 2008-05-15
I did that. I clicked the checkbox next to wine and then selected completely remove or something of that sort and wine still appears in the main menu along with the windows programs that I supposedly removed using wine.

---

### Post by dschaller on 2008-05-15
If I remember correctly, when wine is removed it doesn't completely uninstall its menu icons. In order to erase those, you have to go to the ~/.local/share/applications directory and then delete the wine directory there. Something like this:

cd ~/.local/share/applications
rm -rf wine

Then logout and log back into gnome and the wine menu should be gone.

---

### Post by ryanconnarton on 2008-05-18
I dont know how to enter that or which parts to enter at what time. Could you detail that more? I am only fammilar with Cisco router commands.

---

### Post by dschaller on 2008-05-20
You have to use the terminal command prompt. Look under Applications/Accessories for a program called "Terminal" and open it. Then enter those commands there to delete the wine directory.

---

### Post by ibuclaw on 2008-05-20
The locations of the wine folders would be
```
~/.wine
```
and some scattered files across
```

~/.local/share/applications
~/.local/share/desktop-directories
~/.local/share/icons

```

To go straight to them, press "**Alt+F2**" and type in "**nautilus /path/**".
Where /path/ is one of the above.

Regards
Iain

---

