---
title: "Problem with module-init-tools package"
date: 2014-06-21
forum: General Help
---

### Post by Mansi_M on 2014-06-21
[SIZE=2][FONT=arial]I am new to Ubuntu and currently learning to write Linux kernel modules. [COLOR=#333333]Just to make sure that I have all the correct tools installed, I ran the command "$depmod -v" following a documentation. Instead of the version number, I got a big log of warnings (or maybe, errors).[/COLOR]
[COLOR=#333333]Part of it looked like this:[/COLOR]

[COLOR=#333333]/lib/modules/3.13.0-24-ge[/COLOR][COLOR=#333333]neric/kernel/net/appletal[/COLOR][COLOR=#333333]k/appletalk.ko needs "unregister_snap_client": /lib/modules/3.13.0-24-ge[/COLOR][COLOR=#333333]neric/kernel/net/802/psna[/COLOR][COLOR=#333333]p.ko[/COLOR]
[COLOR=#333333]depmod: ERROR: openat(/lib/modules/3.13.0-24-generic, modules.dep.tmp, 1101, 644): Permission denied

How do I fix this? Will I need to re-install and download the module-init-tools package? If yes, kindly help me with the procedure.

Thanks... [/COLOR][/FONT][/SIZE]

---

