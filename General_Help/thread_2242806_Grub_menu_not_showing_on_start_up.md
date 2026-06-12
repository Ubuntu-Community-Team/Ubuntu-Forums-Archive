---
title: "Grub menu not showing on start up"
date: 2014-09-04
forum: General Help
---

### Post by christon74 on 2014-09-04
Hello fellow ubunters. 
I have just tried the gedit command (gksudo gedit /etc/default/grub) and here is what i get:
(gedit 3232) gtk WARNING**: calling Inhibit failed: GDBus. Error: org.freedesktop.DBus. Error.ServiceUnknown: The name org.gnome. SessionManager was not provided by any.service files

This leaves me...totally nonplussed. 

Thanks in advance for any help.

Chris.

---

### Post by ibjsb4 on 2014-09-04
You didn't say what version your running.

---

### Post by christon74 on 2014-09-04
Hello ibjsb4 :)_ problem solved. I am running Ubuntu 14.04 LTS on an old hp compaq nc 4200. Problem was Ubuntu was loading without letting me choose advance options or the recovery mode when I needed it. Solution: install grub-coreboot-bit. That is what I have just done using synaptic.

---

