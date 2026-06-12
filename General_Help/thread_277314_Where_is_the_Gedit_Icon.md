---
title: "Where is the Gedit Icon?"
date: 2006-10-14
forum: General Help
---

### Post by fatsheep on 2006-10-14
Go to *Applications>Accessories* and add gedit to the panel.  Now right click on the panel icon for gedit, and go to properties (screenshot attached).  Suppposedly "no icon", yet there is one.  I've done a search for gedit images but all it turned up were the alternate logos.  Where is the default gedit icon and why does the launcher say it has no icon when it does?

---

### Post by taurus on 2006-10-14
Most of the icons are in /usr/share/pixmaps!!!

---

### Post by CatKiller on 2006-10-14
The **launcher** may have no icon, even if GEdit normally does. "No icon" in this context meaning that it uses the default application icon.

GEdit uses the icon "text-editor", and the icon that this refers to changes with the theme. If you edit the .desktop file for your launcher and put in Icon=text-editor then you'll get the appropriate icon for the theme you're using.

Or I haven't read your question properly again ;)

EDIT: The jump that I made probably isn't that clear - the Properties page for the launcher is a bit lame in that it doesn't give you very much information about the launcher. It's great if you want to use a particular command with a particular icon, but it doesn't seem to be capable of parsing the correct icon in the same way that the Gnome environment proper can do, nor does it have a way to specify the generic name for the icon in the same way that editing the .desktop file manually can do. Nor can you change the displayed name for locales other than your own, and so on. HTH.

---

### Post by fatsheep on 2006-10-14
> **CatKiller said:**
> The **launcher** may have no icon, even if GEdit normally does. "No icon" in this context meaning that it uses the default application icon.

GEdit uses the icon "text-editor", and the icon that this refers to changes with the theme. If you edit the .desktop file for your launcher and put in Icon=text-editor then you'll get the appropriate icon for the theme you're using.

Or I haven't read your question properly again ;)

EDIT: The jump that I made probably isn't that clear - the Properties page for the launcher is a bit lame in that it doesn't give you very much information about the launcher. It's great if you want to use a particular command with a particular icon, but it doesn't seem to be capable of parsing the correct icon in the same way that the Gnome environment proper can do, nor does it have a way to specify the generic name for the icon in the same way that editing the .desktop file manually can do. Nor can you change the displayed name for locales other than your own, and so on. HTH.

Thanks for the info.  Where would the text-editor icon be located?  A beagle search and a look through /usr/share/pixmaps turned up nothing.

---

### Post by CatKiller on 2006-10-14
> **fatsheep said:**
> Thanks for the info.  Where would the text-editor icon be located?  A beagle search and a look through /usr/share/pixmaps turned up nothing.

You may have as many versions as you have themes. ~/.icons/<theme>/<size>/apps is one possibility, as is /usr/share/icons/<theme>/<size>/apps.

---

### Post by taurus on 2006-10-14
```

/usr/share/pixmaps$ ls -l gedit*
-rw-r--r-- 1 root root  3966 2006-07-31 21:02 gedit-icon.png
-rw-r--r-- 1 root root  4122 2006-07-31 21:02 gedit-icon.xpm
-rw-r--r-- 1 root root 12586 2006-07-31 21:02 gedit-logo.png
-rw-r--r-- 1 root root  3732 2006-07-31 21:02 gedit-plugin-manager.png
/usr/share/pixmaps$

```

---

### Post by fatsheep on 2006-10-14
> **CatKiller said:**
> The **launcher** may have no icon, even if GEdit normally does. "No icon" in this context meaning that it uses the default application icon.

GEdit uses the icon "text-editor", and the icon that this refers to changes with the theme. If you edit the .desktop file for your launcher and put in Icon=text-editor then you'll get the appropriate icon for the theme you're using.

Or I haven't read your question properly again ;)

EDIT: The jump that I made probably isn't that clear - the Properties page for the launcher is a bit lame in that it doesn't give you very much information about the launcher. It's great if you want to use a particular command with a particular icon, but it doesn't seem to be capable of parsing the correct icon in the same way that the Gnome environment proper can do, nor does it have a way to specify the generic name for the icon in the same way that editing the .desktop file manually can do. Nor can you change the displayed name for locales other than your own, and so on. HTH.

> **taurus said:**
> ```

/usr/share/pixmaps$ ls -l gedit*
-rw-r--r-- 1 root root  3966 2006-07-31 21:02 gedit-icon.png
-rw-r--r-- 1 root root  4122 2006-07-31 21:02 gedit-icon.xpm
-rw-r--r-- 1 root root 12586 2006-07-31 21:02 gedit-logo.png
-rw-r--r-- 1 root root  3732 2006-07-31 21:02 gedit-plugin-manager.png
/usr/share/pixmaps$

```

Notice none of those are the default icon for gedit.  

[quote=CatKiller]
You may have as many versions as you have themes. ~/.icons/<theme>/<size>/apps is one possibility, as is /usr/share/icons/<theme>/<size>/apps.
[/quote]
~/.icons/ has no folders or files in it.  I've done a thorough search through /usr/share/icons/Human/ and haven't found the icon...  :-?

---

### Post by tmahmood on 2006-10-14
If you are using the default Ubuntu Icon theme you should also look in the tango folder since many human icons are used from that theme...

if you are using a different theme then you can look inside the appropriate folder 

You can look for Icons in three places
1. /usr/share/icons > all the icon themes are located here
2. /usr/share/pixmaps >some old icons are here...
3. ~/.icons >icons installed by the user are located here..

hope this helps

---

### Post by fatsheep on 2006-10-14
> **tmahmood said:**
> If you are using the default Ubuntu Icon theme you should also look in the tango folder since many human icons are used from that theme...

if you are using a different theme then you can look inside the appropriate folder 

You can look for Icons in three places
1. /usr/share/icons > all the icon themes are located here
2. /usr/share/pixmaps >some old icons are here...
3. ~/.icons >icons installed by the user are located here..

hope this helps

Ah it was in tango, thanks for the help. :)

---

