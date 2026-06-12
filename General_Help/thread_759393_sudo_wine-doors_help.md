---
title: "sudo wine-doors help"
date: 2008-04-19
forum: General Help
---

### Post by Greenducky on 2008-04-19
So when i click on wine-doors in the menu nothing happens,
and when i press alt+f2 and then type wine-doors nothing happens.

but when i open a terminal and type sudo wine-doors this is the output i get

mint@mint-desktop:~$ sudo wine-doors
Debug: Opened log file: wine-doors.log
Debug: in path: /home/mint/.wine-doors
Started logging session
Debug: Xoring all/installed to create available
Checking wine drive: /home/klattimer/.wine/
Debug: wine.py: CheckDrive: Found folder /home/klattimer/.wine/
Debug: wine.py: CheckDrive: Found folder ~/.wine-doors/
Debug: wine.py: CheckDrive: Didn't find file /home/klattimer/.wine/wine-doors/configured
wine.py: CheckDrive: No wine-drive defined in specified wineroot
/usr/share/wine-doors/src/ui.py:964: GtkWarning: Unable to locate theme engine in module_path: "pixmap",
self.widgets = gtk.glade.XML( glade, window_name )


so i tried to uninstall and reinstall and that wont work.
can someone please tell me what i am doing wrong,

---

### Post by zvacet on 2008-04-19
```
sudo apt-get remove --purge wine-doors
```

or 

```
sudo dpkg --remove --force-remove-reinstreq wine-doors
```

It is deb. file and it will be normal to install it by double click on it.

---

