---
title: "Error/warning messages upon starting app in terminal"
date: 2007-02-26
forum: General Help
---

### Post by r0ck80y on 2007-02-26
Hi,

When i start an application thru terminal i get the following messages in the terminal :
```
(process:13875): Gdk-WARNING **: locale not supported by Xlib

(process:13875): Gdk-WARNING **: cannot set locale modifiers

(gftp-gtk:13875): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gftp-gtk:13875): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gftp-gtk:13875): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
:
: (several times)
:
(gftp-gtk:13875): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```
What could they mean? There's isn't any problem in running the app though.
I have xubuntu with kubuntu-desktop installed ( no gnome)
Also in xfce, when i press alt+F2, the run-command window appears and then crashes; hence i have to run all apps thru the console

a li'l help here..thanx :)

---

### Post by nereid on 2007-02-26
The X Error messages are kind of normal. This is something of the Xserver, nothing to worry about, just happens if you start a GTK or Qt application from the console.

The Gdk warnings are about missing locales also nothing to worry about. But the GTK warnings tell you that there are some errors in the GTK theme you are using at the moment. They don't do anything but tell you that the current GTK theme is not 100% correct.

---

