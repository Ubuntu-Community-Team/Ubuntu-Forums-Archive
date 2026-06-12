---
title: "Become Root in Gnome"
date: 2005-11-01
forum: General Help
---

### Post by johnfarrow on 2005-11-01
I am trying to save a file in gedit and I need to be able to become "Root" status.  Is this possible in GUI?

Thanks

---

### Post by teddy69 on 2005-11-01
just gotta run gedit with sudo

```
sudo gedit
```

---

### Post by canadianwriterman on 2005-11-01
[QUOTE=johnfarrow]I am trying to save a file in gedit and I need to be able to become "Root" status.  Is this possible in GUI?

Thanks[/QUOTE]

I'm not at my Breezy machine at the moment, but I suggest going to (I think) Applications > System Tools > Run as another user. In the windows, type "nautilus." This opens Nautilus as root and enables you to use gedit and save it to a root-only directory. This also handy for copying files to other directories where you don't have permission.

---

### Post by 23meg on 2005-11-01
The following tricks will help you:

[http://ubuntuforums.org/showthread.php?t=24008](http://ubuntuforums.org/showthread.php?t=24008)
[http://www.ubuntuforums.org/showthread.php?t=75610](http://www.ubuntuforums.org/showthread.php?t=75610)

---

### Post by johnfarrow on 2005-11-01
OK,
I went to terminal and entered gksudo "gnome-open %u"

What next?

---

### Post by aysiu on 2005-11-01
Huh?
You don't have to be in terminal.
Run this command from the "Run" dialogue:
```
gksudo nautilus
``` and you can browse around and edit files as root.

---

### Post by SickTwist on 2005-11-02
[QUOTE=johnfarrow]I am trying to save a file in gedit and I need to be able to become "Root" status.  Is this possible in GUI?

Thanks[/QUOTE]

Three ways:

1. If you have a terminal open, just type "sudo gedit" (without quotes).

2. Applications --> System Tools --> Run as Different User

enter "gedit" (without quotes) and select "root" from the user list.

3. press ALT+F2 and run the command "gksudo gedit".

Hope that helps :)

PS For any of this to work, you must be logged in as a user with administrator priviledges.

---

