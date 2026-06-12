---
title: "[SOLVED] xorg.conf"
date: 2007-11-19
forum: General Help
---

### Post by f37u5g0d on 2007-11-19
When I try to open the xorg.conf file from a command line ( gksudo gedit /etc/x11/xorg.conf it opens up a file that is named xorg.conf but it is blank and it cannot be saved.  Also behind gedit in the command prompt I have the following output

"~$ gksudo gedit /etc/x11/xorg.conf  <- My input

(gksudo:6435): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(gedit:6436): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
"

There is no "murrine" directory, I looked.  Also there is a file named xorg.conf in the directory etc/x11.  If I open a window navigator with gksudo nautilus so it has root privileges I can alter the file and save it.  Why does it not show up with the usual command line?

---

### Post by JasonF on 2007-11-19
Filenames are case sensitive, the file you are trying to edit is /etc/**X**11/xorg.conf.

---

### Post by minus198 on 2007-11-19
And my question: Why use graphical texteditors? Its better to use, less mouseusage..

sudo nano /etc/X11/xorg.conf

---

### Post by por100pre1 on 2007-11-19
> **JasonF said:**
> Filenames are case sensitive, the file you are trying to edit is /etc/**X**11/xorg.conf.

Yes, type uppercase X in X11. The other errors are related to the GNOME theme currently used, there are nothing to worry about if the theme just looks fine. :)

---

