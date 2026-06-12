---
title: "power off problem Ubuntu 14.04 LTS"
date: 2015-07-10
forum: General Help
---

### Post by baterson on 2015-07-10
Hi guys. I have problem with my notebook (packard bell EasyNote ENTF71BM)
when i use shutdown, halt, reboot, it won't shut down. I tryed shutdown -P now, and other keys. Tryed turn on 'wake on lan' in bios. Change grub config in this line 'GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nomux=1 i8042.noloop=1"' 
All this does not help. I took the advice from here [http://ubuntuforums.org/showthread.php?t=2217602&page=4](http://ubuntuforums.org/showthread.php?t=2217602&page=4)
Help me plz

---

### Post by baterson on 2015-07-14
Guys! I found the solution, added this:
[COLOR=#233039][FONT=Verdana]blacklist dw_dmac
blacklist dw_dmac_core[/FONT][/COLOR]
to /[COLOR=#233039][FONT=Verdana]etc/modprobe.d/blacklist.conf[/FONT][/COLOR]

---

