---
title: "Edgy live cd fails to start X server"
date: 2007-06-18
forum: General Help
---

### Post by cptjaben on 2007-06-18
I'm trying to install Edgy on my laptop, but when i run the live cd and starts to boot up it cannot start the X server, and I have only command line avaible. My video card is an ATI X1700, and i'm wondering if there is a way to fix this problem or if there's a way to install ubuntu via the command line ( as opposed to clicking install on the desktop of the Live cd)? Thanks.

---

### Post by zvacet on 2007-06-18
```
sudo dpkg-reconfigure xserver-xorg
```

select **vesa** driver to get graphic and after that find and install drivers for your card.

---

### Post by cptjaben on 2007-06-18
After doing this and restarting Gnome Desktop Manager, it attempts to start X and on the third time it gives me the same screen saying it failed to start the X server. Any ideas anyone?

---

### Post by zvacet on 2007-06-18
```
sudo /etc/init.d/gdm start
```

---

### Post by cptjaben on 2007-06-18
that's the command I've been using to restart, which has been causing the 2nd X server failure, any other ideas?

---

### Post by Crafty Kisses on 2007-06-18
> **cptjaben said:**
> that's the command I've been using to restart, which has been causing the 2nd X server failure, any other ideas?

Have you tried backing up your X server file?

---

### Post by cptjaben on 2007-06-18
how do i do that, remember i'm running off a live cd

---

