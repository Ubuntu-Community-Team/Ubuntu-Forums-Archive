---
title: "Odd menu behavior after installing beryl"
date: 2007-01-20
forum: General Help
---

### Post by Rollotamasi on 2007-01-20
I just finished installing beryl and it I am now experiencing some odd window/mouse/menu behavior.  If I have just one program open on screen at a time everything is fine.  But if I have more then one window open at a time I cant open any menus, or right click to bring up a menu to cut and paste.  Anyone have any ideas how to fix this?  ALso, If I have a window open, the menus from my taskbar always appear behind the window that is open.


Thanks!

---

### Post by wpshooter on 2007-01-20
I believe I have heard this kind of complains before, that is why I don't install this software !!!

---

### Post by daradib on 2007-01-20
I have a similar problem.
If I have Beryl Manager set to launch the KWin Window Manager in case of crashing, Beryl will crash and the KWin Windows Manager will take over my open windows under the following circumstances regardless of if I have zero, one, or several windows open:
I do the following with my kicker:
[SIZE="3"]Right Click[/SIZE]
Taskbar including tasks/windows present on the taskbar
Trash
Clock
System Tray but not the icons present in the system tray
Desktop Preview and Pager
Konqueror Button
Kontact Button
System Menu
K Menu
[SIZE="3"]Left Click:[/SIZE]
Trash
System Menu
K Menu

I am using Kubuntu 6.10 Edgy 64-bit
ATI Radeon X800 PCI-E Graphics card with fglrx drivers
AMD Athlon64

---

### Post by mcduck on 2007-01-20
Positioning menus behind windows is a bug that sometimes happens with Beryl. It's in early development stage so small issues like this can be expected. Most likely it will get fixed sooner or later.

Anyway, when that happens right-click on the Beryl icon in notification area and select 'Reload Window Manager'. This always fixes the problem for me.

---

### Post by Rollotamasi on 2007-01-20
Didn't even think about something as simple as reloading the window manager. Tried it and works fine.  Thanks for the suggestion.

---

