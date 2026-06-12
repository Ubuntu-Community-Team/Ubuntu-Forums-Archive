---
title: "Help config grub-reboot in sudoer.d file, so I don't need to use &quot;sudo&quot; every time"
date: 2022-10-06
forum: General Help
---

### Post by drench0084 on 2022-10-06
Hello, i was trying to config the "grub-reboot" command in the sudoers.d file, because i don't want to use the root password every time, searching a bit i came across this setup
> [FONT=monospace][COLOR=#000000]~# [FONT=monospace][COLOR=#000000]sudo visudo -f /etc/sudoers.d/grub-reboot-config[/COLOR][/FONT]
Cmnd_Alias     COMMAND = /usr/sbin/grub-reboot [/COLOR]
Cmnd_Alias     FILES = /usr/sbin/grub-probe, /boot/grub/grubenv 
Cmnd_Alias     GRUB = COMMAND, FILES 
%grub-reboot-group ALL=GRUB
[/FONT]
but, it isn't working, and show this output
> ~$ grub-reboot 0
/usr/sbin/grub-probe: warning: disk does not exist, so falling back to partition device /dev/sda1.
/usr/sbin/grub-probe: warning: disk does not exist, so falling back to partition device /dev/sda1.
/usr/sbin/grub-probe: warning: disk does not exist, so falling back to partition device /dev/sda1.
/usr/sbin/grub-probe: error: disk `hostdisk//dev/sda1' not found.
/usr/bin/grub-editenv: error: cannot open `/boot/grub/grubenv': Permission denied
what i did wrong here, and how i correct it?

NOTE:
> ~$ groups
viniciusmd adm cdrom sudo dip plugdev lpadmin sambashare grub-reboot-group
my user(viniciusmd) is in the group that i created for the grub-reboot(grub-reboot-group)

Thanks you all very much!

---

