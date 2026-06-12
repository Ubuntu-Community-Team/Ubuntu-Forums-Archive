---
title: "Need helping getting X to work"
date: 2007-12-26
forum: General Help
---

### Post by JarvidLol on 2007-12-26
K:(, I loaded the ATI 3D acceleration drivers and when I reboot'D it loaded normally but the screen was just dark and I couldn't see anything. How can I change it back or make it work?

Things I have tried 
Adjusting the moniter
Accessing the ubuntu forums for help; haven't recieved any yet, though

Things I will try 
Viewing the xorg logs
Trying a different moniter

          :( :(

---

### Post by taurus on 2007-12-26
Boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure -phigh xserver-xorg
```
Then, reboot with

```
shutdown -r now
```

---

### Post by JarvidLol on 2007-12-26
> **taurus said:**
> Boot into recovery mode from GRUB menu and reconfigure your X again with


That has do with me loading restricted 3D drivers right?

---

### Post by DeathOnJuice on 2007-12-26
Correct. Pretty much, a line in your /etc/X11/xorg.conf was changed to instruct Ubuntu to use the new driver. The command the other user posted is a tool to change it back.

---

### Post by t3hi3x on 2007-12-27
I've had nothing but bad luck with ATI's 3D drivers. Try using envy:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

to install the drivers. The guy made it so much easier than it use to be.

Report on how that goes.

---

### Post by JarvidLol on 2007-12-27
> **DeathOnJuice said:**
> Correct. Pretty much, a line in your /etc/X11/xorg.conf was changed to instruct Ubuntu to use the new driver. The command the other user posted is a tool to change it back.

Thats what I thought, although when I usually mess up my xorg.conf I diagnose the problem by booting into slax and editing it manually.

Thanks for the link to envy as well.

---

