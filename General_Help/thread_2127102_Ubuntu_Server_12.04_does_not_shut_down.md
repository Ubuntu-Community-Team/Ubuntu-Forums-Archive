---
title: "Ubuntu Server 12.04 does not shut down"
date: 2013-03-19
forum: General Help
---

### Post by dimedia on 2013-03-19
Hello,

I have a old Fuijtsu Siemens Scenic 300 PC with Ubuntu server on it. All works fine, but when I type "poweroff", it stopps at [xx.xxx] System halted....

So I added acpi=force to this line [COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" in /etc/default/grub.

But this doesn't work, it stopps again at System halted.

Befor Ubuntu, there was CentOS installed, and i added acpi=force to the kernel line in the Grub conf and it worked, but then the pc crasched on booting.

Hope you can help me.

Thanks

-Update-
I followed this guide and it worked: [/COLOR]http://rahulchand.blogspot.co.at/2011/05/ubuntu-910-system-halted-on-shutdown.html

---

