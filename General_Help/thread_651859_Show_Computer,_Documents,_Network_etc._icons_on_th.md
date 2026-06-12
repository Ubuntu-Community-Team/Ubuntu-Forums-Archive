---
title: "Show Computer, Documents, Network etc. icons on the Kubuntu desktop"
date: 2007-12-28
forum: General Help
---

### Post by parampreet on 2007-12-28
A stupid n00b question but, how do I get Kubuntu Gutsy to show the standard icons on the desktop like Computer, Documents, Network, Trash etc.?

---

### Post by nunnst on 2007-12-28
Just drag and drop!  Example, and menu item in Gnome can be clicked and dragged to the desktop. Same for your folders in Nautilus.    

Hope this helps.

---

### Post by nunnst on 2007-12-28
Opps, your running KDE...I assume it has many of the same features as Gnome, but never used it so not sure if the above will work for you.

---

### Post by parampreet on 2007-12-28
I did manage to get the Computer, Home and Network icons by right-clicking on the desktop, selecting "Create New" -> "Link to Location (URL)..." and putting "system:/", "home:/" and "remote:/" as URLs for the Computer, Home and Network icons respectively. I tried the same for the Trash icon (trash:/) and the icon appeared on the desktop, but the icon seems to be a "static" icon. For instance, when I empty the Trash bin, it still shows the same "Trash full" icon.
Any pointers on this?

---

### Post by BoeBoe on 2008-02-24
Ditto, my trash bin on dekstop doesn't behave like it should... :confused:

---

### Post by BoeBoe on 2008-02-25
Fixed it :)
1. Right-click on bin
2. Select 'open with'
3. Choose your text editor, e.g: kate
4. edit it as below:

[Desktop Entry]
Encoding=UTF-8
Icon=trashcan_full
EmptyIcon=trashcan_empty
Type=Link
URL=trash:/

---

