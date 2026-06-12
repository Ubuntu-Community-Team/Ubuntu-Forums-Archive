---
title: "sudo  nautilus"
date: 2016-02-22
forum: General Help
---

### Post by cutano on 2016-02-22
Been getting this warning in terminal when I type "sudo nautilus"


(nautilus:6134): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: 
The name org.gnome.SessionManager was not provided by any .service files

Ubuntu 14.04

Thank you

---

### Post by QDR06VV9 on 2016-02-22
Starting any GUI application with sudo is not the best or safest way to call it.
Instead use gksudo to call any GUI application

> You should never use normal sudo to start graphical applications as root. You should use gksudo (kdesudo on Kubuntu) to run such programs. gksudo sets HOME=/root, and copies .
Xauthority to a tmp directory. This prevents files in your home directory becoming owned by root.
Just some friendly advice is all..:D
Kind regards

---

### Post by cutano on 2016-02-22
Now I understand. Thanks for the info. Im guessing since I didnt use it to write any files I most likely didn't screw anything up.

---

### Post by Mopar1973Man on 2016-02-22
Learning question? 

Why would you want to call sudo on a program like that?

---

### Post by CaptainMark on 2016-02-23
That's a bit like asking why you would call sudo cp or sudo mv, there are infinite reasons why you would do those, just that some people feel more comfortable with GUI, it's just the OP didn't know not to use sudo with graphical programs.

---

