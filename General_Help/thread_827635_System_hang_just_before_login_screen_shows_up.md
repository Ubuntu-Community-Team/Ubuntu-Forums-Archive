---
title: "System hang just before login screen shows up"
date: 2008-06-13
forum: General Help
---

### Post by luizlizard on 2008-06-13
Yesterday i reinstalled ubuntu to have a clean 8.04 install, so i finished setup, rebooted, logged in enable restricted drivers, rebooted, and got as normal again, the i was asked to update the system. It installed 160 updates then i rebooted. But this time the system got stuck with the loading cursor on a black screen, it stops there, the mouse works, i can switch to any tty and they all work, but i cant get it to showup the login screen...

Any ideas?

---

### Post by Victormd on 2008-06-13
If you installed all the updates, then you probably got new kernels installed as well. Have you tried booting to a previous kernel (should be listed in the grub menu) to see if you have the same problem?

---

### Post by luizlizard on 2008-06-13
Yes, i tried both kernels with no luck, both get stuck at the same place, seems to be a problem with gdm, but i just don't know where to look...

---

### Post by luizlizard on 2008-06-13
btw, i tried to fix X in the recovery mode with no luck...

---

### Post by luizlizard on 2008-06-13
any ideas?

---

### Post by FAJALOU on 2008-06-13
try removing gnome from a tty and reinstalling it?  Or try installing another gui, and then from there try to get back to gnome.  Do you want to keep gnome or remove it?  I think that reinstalling gnome would be a good option to take.

---

### Post by aquavitae on 2008-06-13
Can you post the contents of /var/log/xserver.0.log? Also the output of "tail dmesg"

---

### Post by luizlizard on 2008-06-13
> **aquavitae said:**
> Can you post the contents of /var/log/xserver.0.log? Also the output of "tail dmesg"

/var/log/xserver.0.log does not exist and tail dmesg, has no relevant information...

---

### Post by luizlizard on 2008-06-13
> **aquavitae said:**
> Can you post the contents of /var/log/xserver.0.log? Also the output of "tail dmesg"

/var/log/xserver.0.log does not exist and tail dmesg, has no relevant information...

[QUOTE=FAJALOU]try removing gnome from a tty and reinstalling it? Or try installing another gui, and then from there try to get back to gnome. Do you want to keep gnome or remove it? I think that reinstalling gnome would be a good option to take.[/QUOTE]

i tried to reinstall it from aptitude, but i don't know which package can reinstall the complete gnome, because it's split in multiple packages, any idea for this?

---

### Post by avtolle on 2008-06-13
Ubuntu-desktop is the meta-package that will reinstall all of Gnome.

---

### Post by luizlizard on 2008-06-13
i found Xorg.0.log, it's attached.

---

### Post by luizlizard on 2008-06-14
anyone?

---

### Post by aquavitae on 2008-06-14
Sorry, I got the wrong file name! The last line of that file looks like the error:
> [config/hal] couldn't initialise context: (null) ((null))
But I'm not sure what exactly it means. Can you post /etc/X11/xorg.conf? I don't know if it will help, but it may show something important... What video card do you have, and which drivers are you using? From the log file you posted it looks like you have an nvidia card, but are you using the restricted drivers or just the default built in ones? If you're using the restricted ones you could try unloading them.

---

### Post by luizlizard on 2008-06-15
> **aquavitae said:**
> Sorry, I got the wrong file name! The last line of that file looks like the error:

But I'm not sure what exactly it means. Can you post /etc/X11/xorg.conf? I don't know if it will help, but it may show something important... What video card do you have, and which drivers are you using? From the log file you posted it looks like you have an nvidia card, but are you using the restricted drivers or just the default built in ones? If you're using the restricted ones you could try unloading them.

yes a GeForce Go 7700, and im using restricted drivers, but i don't think they are the problem because they do get loaded and the mouse appears, at correct resolution...

Attached is xorg.conf

Thanks!!

---

### Post by luizlizard on 2008-06-16
bump..

---

### Post by aquavitae on 2008-06-16
I'm not too sure what to suggest next... I suspect it may have something to do with the restriced drivers, but that's just a guess. Try uninstalling them and see if that helps.  Btw, can you start the xserver manually? Start up in recovery mode, drop to the console and type 'startx'. Also, according to the man page 'Xorg -configure' will generate an xorg.conf file. Maybe give that a try and see what the xorg.conf it generates contains. There might be a clue there.

---

### Post by iceburnt on 2009-04-19
I installed ubuntu 8.10 inside windows yesterday and im having the same problem. Just before the login screen the screen goes orange and the mouse gets stuck on the loading cursor

---

