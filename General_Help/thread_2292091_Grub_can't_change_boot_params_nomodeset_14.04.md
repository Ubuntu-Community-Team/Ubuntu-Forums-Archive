---
title: "Grub can't change boot params nomodeset 14.04"
date: 2015-08-25
forum: General Help
---

### Post by compilerone on 2015-08-25
Hi :) 
I am trying to update my kernel boot parameters
by modifying /etc/default/grub
and changing the line GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
then running command sudo update-grub

the system when booting does not see this change, I can hold shift to get to grub, go 'e' on the default menu item and it shows the linux line without my nomodeset setting, its not there! but I can edit it manually and boot with this setting.

I also tried to modify /etc/grub.d/10_linux and add in nomodeset to the end of the linux lines in there, with no result.

this is ubuntu 14.04.3-desktop-amd64

thanks,

---

### Post by ajgreeny on 2015-08-25
Can we check that you do not have more than one Linux OS on the machine and that another OS is actually the one that is providing and managing grub on the system.  It seems unlikely, but it could explain what is happening.

Are you opening /etc/default/grub as root and then saving the edited file before running sudo update-grub?  You must do that or the system will make no changes to grub.

---

### Post by compilerone on 2015-08-25
thanks, this is fixed now, the issue was that i was in single user mode and it was updating the recovery kernel, i booted into normal mode and update-grub from there updated the proper running kernel.

---

