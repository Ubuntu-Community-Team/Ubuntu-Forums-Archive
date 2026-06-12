---
title: "Mouse not Working"
date: 2008-04-16
forum: General Help
---

### Post by SoulDog on 2008-04-16
When I start up my computer it works for a few minutes, but then the mouse stops working. It's a USB Logitech(I Think). Is there any way to fix it?

I'm new to linux and don't know what feisty and kernal and all that other stuff means.

---

### Post by nicedude on 2008-04-16
I saw this link to someone having similar problems.

[http://ubuntuforums.org/showthread.php?t=359482](http://ubuntuforums.org/showthread.php?t=359482)

solution was 2 commands to reactivate your mouse without rebooting

Since you said you dont know anything about linux you open a terminal window (applications -> accessories -> terminal) this will give you a command line, then copy and paste these 2 commands one at a time in the terminal and press enter, these run with the sudo prefix which means these commands run as root, so you will be asked for your password to execute them.
 
sudo rmmod ohci-hcd
sudo modprobe ohci-hcd no_handshake=1

if your problem is the same as theirs then this should fix it untill you reboot, then you would have to do this again.

---

