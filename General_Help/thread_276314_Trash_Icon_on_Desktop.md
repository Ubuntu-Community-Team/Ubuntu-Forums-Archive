---
title: "Trash Icon on Desktop"
date: 2006-10-12
forum: General Help
---

### Post by ricanelite on 2006-10-12
Hello all! New to Ubuntu Linux, and I have to say I'm enjoying it very much. 

Now my main thing is it possible to put my trash bin icon on the desktop. Also is it possible to change my desktops icons font colors like to black.

Also I'm using the KDE Desktop and completely new to Linux and Ubuntu but I am willing to learn as much as I can.

Hope you all here could help me out. Thank you!!:)

---

### Post by kuja on 2006-10-12
Right click on the desktop: Create new > Link to location
Name should be Trash (or whatever you prefer)
Make location trash:/

And voila, good to go.

Edit: Almost missed something

To change the text color for desktop icons:

right click on the desktop > configure
In the background tab, click on the advanced button
There's a Background Icon Text section that should do it for you.

---

### Post by MintabiePete on 2006-10-12
Thats handy to know  for the KDE desktop , thanks  kuja :)  What about the  gnome  desktop ? is there a way to put a trashcan on the  desktop  when the old one has been deleted , not on the taskbar but the desktop .

Edit: I can right click on the  desktop in gnome , create  launcher , name it trash or whatever I want , put trash:/ in command  and  Type , change it to link  and it  works  , but not too sure how  to get the icon for trashcan :)

---

### Post by GStubbs43 on 2006-10-12
> **MintabiePete said:**
> Thats handy to know  for the KDE desktop , thanks  kuja :)  What about the  gnome  desktop ? is there a way to put a trashcan on the  desktop  when the old one has been deleted , not on the taskbar but the desktop .

Edit: I can right click on the  desktop in gnome , create  launcher , name it trash or whatever I want , put trash:/ in command  and  Type , change it to link  and it  works  , but not too sure how  to get the icon for trashcan :)

In GNOME, press alt+F2 and type gconf-editor then go to apps>nautilus>desktop and check off "trash_icon_visible" and voila!

---

### Post by dagnabit dang doohickey on 2006-10-12
Press <Alt>F2 and run gconf-editor

Work your way through these folders: apps > nautilus > desktop

In the window on the right, check the box for trash_icon_visible

[*GStubbs43 beat me to it*]

---

### Post by MintabiePete on 2006-10-12
Thank you both for your quick response :)

---

### Post by Genican1 on 2006-10-18
> **GStubbs43 said:**
> In GNOME, press alt+F2 and type gconf-editor then go to apps>nautilus>desktop and check off "trash_icon_visible" and voila!

hey, thanks, that's  great help!

---

