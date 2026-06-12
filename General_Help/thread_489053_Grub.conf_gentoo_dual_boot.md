---
title: "Grub.conf gentoo dual boot"
date: 2007-06-30
forum: General Help
---

### Post by rustysail on 2007-06-30
Hey guys I'm trying to dual boot gentoo with fiesty.  I need to locate the kernel in Ubuntu in order to write my grub.conf file though.  I feel stupid for not know where it is, but it isn't in the same place as Gentoo's.  Thanks for the help.

Rusty.

---

### Post by confused57 on 2007-06-30
You could add an entry to boot Ubuntu to your Gentoo grub, using configfile:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

Ubuntu uses /boot/grub/menu.lst, instead of /boot/grub/grub.conf

---

