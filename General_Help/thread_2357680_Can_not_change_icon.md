---
title: "Can not change icon"
date: 2017-04-04
forum: General Help
---

### Post by raleigh3 on 2017-04-04
If I put this on my desktop, I am unable to change it's icon.

Any work around ?

```
#!/bin/bash
# Ubuntu_Mate 16.04
#    
#
#
libreoffice --writer /home/andy/Documents/Hawks_Schedule.odt

```

---

### Post by vasa1 on 2017-04-04
Post a clear image of what you see.

---

### Post by kostkon on 2017-04-04
You could turn it into a desktop file, like this:
```
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Hawks_Schedule.odt
Comment=Hawks Schedule file
Keywords=
Exec=libreoffice --writer /home/andy/Documents/Hawks_Schedule.odt
Icon=/path/to/icon
Categories=
Terminal=false
StartupNotify=true
```
and save it as
```
Hawks_Schedule.odt.desktop
```
on your desktop and then make it executable.

Hope that helps.

---

### Post by raleigh3 on 2017-04-04
Thanks kostkon.

It worked great.

When I right click on a desktop file, there is no option to open with an editor.

I have to do so from a console.

Any work around ?

---

### Post by kostkon on 2017-04-04
> **raleigh3 said:**
> Any work around ?
No, because it's just a desktop shortcut and not the actual file.

Or, if you mean how to edit .desktop files, Gnome, at least, does not give you the option to edit .desktop files when you right-click on them because they are application shortcuts after all and you aren't supposed to be able to modify them.

Only way to edit a .desktop file is to drag-and-drop it into your favourite text editor (or use its open file menu option to locate and open the file).

---

### Post by raleigh3 on 2017-04-05
When I asked the question, it was because I was using Caja.

Thunar is my main file manager and it does allow you to open desktop files with whatever editor you want.

Caja is ok, but nearly as versatile as Thunar.

And Caja also does not you to operate as a superuser.

I love Thunar's custom actions.

---

