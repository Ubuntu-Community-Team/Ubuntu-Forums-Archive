---
title: "One time boot changes to grub"
date: 2007-09-27
forum: General Help
---

### Post by Baka no Kami on 2007-09-27
Is there a way to make temporary changed to the Grub menu from inside Ubuntu?  What I'm looking to do is add an icon to the desktop that will restart the computer and tell Grub to make windows the default menu option, but not make the change permanent.  I have a bluetooth keyboard and mouse and sometimes the connection resets when I restart, so I can't change Grub at boot. When that happens it won't work at boot again untill I hook up an old keyboard, boot to windows, and then restart.

---

### Post by dcstar on 2007-09-28
> **Baka no Kami said:**
> Is there a way to make temporary changed to the Grub menu from inside Ubuntu?  What I'm looking to do is add an icon to the desktop that will restart the computer and tell Grub to make windows the default menu option, but not make the change permanent.  I have a bluetooth keyboard and mouse and sometimes the connection resets when I restart, so I can't change Grub at boot. When that happens it won't work at boot again untill I hook up an old keyboard, boot to windows, and then restart.

Just edit /boot/grub/menu.lst and make Windows the default option - when you boot normally you can use the keyboard to change it to boot Ubuntu.

---

### Post by Baka no Kami on 2007-10-11
> **dcstar said:**
> Just edit /boot/grub/menu.lst and make Windows the default option - when you boot normally you can use the keyboard to change it to boot Ubuntu.

But I'll still run into the same problem, only going the other way.  I'll still have to plug in a USB keyboard to change the option to Ubuntu if the Bluetooth board doesn't happen to be working at boot time. The goal is to leave the default option on Ubuntu but have a way of changing it to Windows that's only good for the next reboot.  That way when I'm done in windows I can just reboot and walk away.

---

### Post by Hegh on 2008-04-11
You might try the procedure outlined here in the GRUB manual:

[http://www.gnu.org/software/grub/manual/html_node/Booting-once_002donly.html#Booting-once_002donly](http://www.gnu.org/software/grub/manual/html_node/Booting-once_002donly.html#Booting-once_002donly)

Basically, instead of new/old kernels, you would have Ubuntu first and Windows second. Both would savedefault to Ubuntu, but your shortcut on the desktop would run 'grub-set-default' to make Windows come up next. Good luck!

PS I was interested so I could tell Ubuntu to reboot into Windows from work, so I don't have to wait for a reboot when I get home. How's that for lazy? :cool:

---

