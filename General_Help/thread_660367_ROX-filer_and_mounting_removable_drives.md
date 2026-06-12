---
title: "ROX-filer and mounting removable drives"
date: 2008-01-06
forum: General Help
---

### Post by Odd-rationale on 2008-01-06
Hello! I've installed fluxbox on top of my Ubuntu installation. I also installed ROX-filer for my file manager. I'm having trouble auto-mounting usb drives.

First of all, I added the gnome-volume-manager to my startup script. This auto-mounts cd fine. But when I try to plug in a usb drive, I get this error message:

> Cannot mount volume.

You are not privileged to mount the volume 'disk'.

I know how to do it from the command line, but using gnome-volume-manager would be a great convenience.

BTW, here's a screen-shot of my current desktop. :)

---

### Post by jeffus_il on 2008-01-12
Install the Rox "Device Handler", this requires pmount which you can install through Synaptic. It mounts automatically, if you set it up in removable media>preferences of the device handler applet. You need to "Eject" and not "Unmount" for some reason.

---

### Post by Odd-rationale on 2008-01-12
OK thanks I'll give that a try,

---

### Post by jeffus_il on 2008-01-13
How do you like this? Rox managing the complete desktop on Hardy, session management, mail applet, weather, Wifi, network applet, and more.

---

### Post by Odd-rationale on 2008-01-13
Hey, that's cool.

Is that the ROX-desktop? or fluxbox/rox-filer combo?

---

### Post by jeffus_il on 2008-01-13
I think it's called OroboRox (the Window Manager)
with Rox-session as the session manager, complete Rox.

---

### Post by Mark76 on 2008-05-15
Looks great.

I love ROX-DE. :)

did you install yours via the ROXAll package or by adding the rox4debian packages to your synaptic?

---

