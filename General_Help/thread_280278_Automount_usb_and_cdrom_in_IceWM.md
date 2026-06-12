---
title: "Automount usb and cdrom in IceWM"
date: 2006-10-19
forum: General Help
---

### Post by seshomaru samma on 2006-10-19
HI
Does anyone know how to make IceWM automount the CDrom and USB key?
I would like it to show a USB icon once I insert a USB and automatically display a CD icon if I put a CD in , or better autoplay the CD.
Thanks

---

### Post by Peter76 on 2006-10-27
I have not looked into icons popping up in Icewm; but with rox you can automount icons by clicking on them, if the directory where the icon points to is in /etc/fstab. Have a look  at my tutorial here to setup icewm with rox:

[http://www.ubuntuforums.org/showthread.php?t=171203](http://www.ubuntuforums.org/showthread.php?t=171203)

---

### Post by pelle.k on 2006-11-11
Thunar automounts devices for me, through hal/dbus, much like nautilus does. Oh, and you don't need to fire up gnome-volume-manager either :)
I run thunar svn though :| (I don't know if thunar in edgy has that ability, but i suggest you try, and please let us know how it worked out for ya...)

---

### Post by seshomaru samma on 2006-11-12
what's hal/dbus?
I have 4 IceWm machines , 3 of them dont automount anything, I put a CD in and I cant browse it at all without mounting it with the terminal ,same for USBs. No Icon pops up. These 3 are Xubuntus
At home I have an Ubuntu with IceWm as desktop manager and have no problem.
The only way I could get my IceWm (and Xubuntu in general) to automount and show an icon is with gnome-volume-manager.

---

### Post by pelle.k on 2006-11-12
hal is the "hardware abstraction layer" and it is commonly used by applications to see what new hardware has been added.
dbus is as communication layer between (modern) apps that let them know what is happening.
udev is responsible for creating device nodes (such as /dev/sda).

This is how it goes.
udev (recognizes new hardware, creates /dev node if needed) tells -> dbus registers this new event. <- hal gets this info and reacts if it is told so by the OS (for example shows your inserted usb drive, and mounts it if you click it. it will tell dbus of what is does also.

At least i think how this is done. correct me if i'm wrong.

I dont know if thunar in edgy is fully functional yet, but until then, use gnome-volume-manager...

---

