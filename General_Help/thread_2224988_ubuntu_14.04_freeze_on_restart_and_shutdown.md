---
title: "ubuntu 14.04 freeze on restart and shutdown"
date: 2014-05-19
forum: General Help
---

### Post by Photorelease on 2014-05-19
Hi all,
i cant restart or shutdown the computer.
already tried

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=bios"[COLOR=#333333][FONT=Ubuntu] 
[/FONT][/COLOR]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash apm=power_off"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=pci"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force apm=power_off"
[COLOR=#333333][FONT=Ubuntu]
even in the terminal, doesnt work
[/FONT][/COLOR]$ sudo shutdown -h now

and always get this message:

> *killing all remaining processes... [fail]
*deactivating swap... [ok]
mount: / is busy
*will now halt

i'm using one dell precision m90.

any idea? thanks all

---

### Post by christo3 on 2014-05-19
Save yourself the trouble and backup your data and .deb packages and do a complete reinstall. if you're not a novice ( like myself) and wan't to learn fixing broken systems , go ahead .

---

### Post by Photorelease on 2014-05-19
yep... but i already did a complete reinstall and the problem keeps the same...

---

### Post by dragonfly41 on 2014-05-19
From a simple google search .. try this .. [http://ocaoimh.ie/2008/02/13/how-to-umount-when-the-device-is-busy/](http://ocaoimh.ie/2008/02/13/how-to-umount-when-the-device-is-busy/)

substitute your ubuntu 14.04 partition .. /dev/sda[COLOR=#ff0000]x[/COLOR] .. in commands

---

