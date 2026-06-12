---
title: "QWERTY forced defualt layout"
date: 2008-04-30
forum: General Help
---

### Post by highstead on 2008-04-30
Recently upgraded to Hardy heron.  Everything seems okay, except my keyboard layout.  I don't use QWERTY, i use Dvorak.  Everything defaults to QWERTY even though under keyboard layouts QWERTY isn't there.  To fix this i have to add a new layout, and then close.  This is a work around, but rather annoying.  Anyone (likely someone using a international layout) have a more solid solution?

Also MX518 mouse i had to remove the lines needed in gutsy to get back/forward working.

---

### Post by highstead on 2008-05-03
Still having this QWERTY problem... any thought would be appreciated.

---

### Post by der_joachim on 2008-05-04
I can tell you how to configure xorg, but I'm told that gnome recognizes that there are different settings and it will nag you until you solve it. Being a KDE user, I cannot help you with the latter.

Anyhoo, to configure xorg, do the following things:
- Make a backup of the file /etc/X11/xorg.conf .
- Make sure that you have root privileges and open xorg.conf in your favourite text editor.
- Find your keyboard section and make sure that the following line 
```

	Option		"XkbLayout"	"us"

```
looks like this:
```

	Option		"XkbLayout"	"us(dvorak)"

```
- Save your file and restart X. You should have the dvorak layout now.

---

### Post by Dyqik on 2008-05-05
I was having a related problem with X always using US layout even though GB was the only layout in the keyboard config gui.  

Running 
```
sudo dpkg-reconfigure xserver-xorg
```

and setting the keyboard layout there fixed this problem.  I had to install the read-edid package to prevent the xorg configure script complaining about a missing get-edid program.

---

### Post by Rhubarb on 2008-06-10
I have found a work-around that will fix this up for you.
Please refer to my post here on a similar thread:
[http://ubuntuforums.org/showpost.php?p=5153726&postcount=3](http://ubuntuforums.org/showpost.php?p=5153726&postcount=3)

---

