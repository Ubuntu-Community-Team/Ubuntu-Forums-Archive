---
title: "Setting up two 22&quot; LCDs and Compiz - Help please"
date: 2007-10-30
forum: General Help
---

### Post by DAE_JA_VOO on 2007-10-30
How's it guys.

Okay, here's the deal. I've got my 7.10 installation up and running perfectly. Drivers for my 7600GT are installed and all is running perfectly. I currently have one 22" LCD at 1680x1050 connected.

Now, i have ANOTHER 22", which i want to have set up with the current one. I also want compiz to work.

Can anyone please help me out?

Last time i tried this i completely screwed up my install. Can't remember what i did but i don't wanna do it again.

Any help will be greatly appreciated :)

---

### Post by kiddyfurby on 2007-10-30
sudo nvidia-settings
enabled twinview for the other monitor

restart x
if there's no windows border, find a line like "addargbvisuals" from xorg.conf's backup, in /etc/X11

---

### Post by kiddyfurby on 2007-10-30
sudo nvidia-settings
enabled twinview for the other monitor, restart x

if there's no windows border, you need to add some options to xorg.conf
the file is in /etc/X11, you might have backups like xorg.conf.1 ...
you can always revert to old xorg.conf in case something broke

---

