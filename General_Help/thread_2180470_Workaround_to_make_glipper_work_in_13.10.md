---
title: "Workaround to make glipper work in 13.10?"
date: 2013-10-13
forum: General Help
---

### Post by volkerbradley on 2013-10-13
I'm aware that there is a bug that keeps glipper from functioning properlly in 13.10.  
Have any of you been able to display the menus of glipper when you right-click on it?

---

### Post by volkerbradley on 2013-10-14
When I installed 13.10 on another computer, glipper worked.  I have no idea why.
Look at [http://youtu.be/T2qzNPDBIew](http://youtu.be/T2qzNPDBIew)
If you have any ideas on how to make glipper work in 13.10, please let me know.

---

### Post by volkerbradley on 2013-10-15
glipper functions as it should on Cinnamon.

---

### Post by jweber53 on 2013-10-20
Clean install of 13.10 on an acer aspire one.

glipper is broken for me, too. It displays in the tray when started from the command line and spits this out:

```

jweber@nardis:~$ glipper
SHARED_DATA_DIR: /usr/share/glipper
Binding shortcut <Ctrl><Alt>c to popup glipper
Changed process name to: glipper
/usr/lib/python2.7/dist-packages/glipper/AppIndicator.py:43: Warning: /build/buildd/glib2.0-2.38.0/./gobject/gsignal.c:2475: signal 'child-added' is invalid for instance '0x1912190' of type 'GtkMenu'
  self._app_indicator.set_menu(self.menu)

```

Then it spits out the following when clicking on the tray icon:


```


(glipper:5806): LIBDBUSMENU-GLIB-WARNING **: About to Show called on an item wihtout submenus.  We're ignoring it.

```

The   <Ctrl><Alt>c mentioned in the output does work for me and glipper is usable that way.

---

### Post by Lorin Ricker on 2013-11-06
+1 to jweber53's answer above. I too just did a clean install 13.10, also (coincidentally) on an Acer Aspire One; glipper starts and breaks exactly as above.

Fortunately, also +1: "[COLOR=#000000]The <Ctrl><Alt>c mentioned in the output does work for me and glipper is usable that way.[/COLOR]"

Hope this extremely useful utility gets some bug-fix attention soon...

---

