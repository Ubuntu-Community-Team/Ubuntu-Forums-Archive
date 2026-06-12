---
title: "Where are tty (1 to 6) conf files in systemd (ubuntu 15.04)?"
date: 2015-04-23
forum: General Help
---

### Post by fprietog on 2015-04-23
Hello,

I have some mods done in the tty 1 to 6 conf files:
[FONT=courier new]
   /etc/init/tty1.conf
   ...
   /etc/init/tty6.conf
[/FONT]
But it seems that these configuration files are not used anymore by systemd (ubuntu 15.04).

Does someone knows what are the systemd equivalent tty conf files?


Thanks and best regards.

---

### Post by dino99 on 2015-04-23
Look at /dev/tty?   [http://0pointer.de/blog/projects/serial-console.html](http://0pointer.de/blog/projects/serial-console.html)
and some ideas from arch [https://wiki.archlinux.org/index.php/Systemd_FAQ](https://wiki.archlinux.org/index.php/Systemd_FAQ)

---

### Post by fprietog on 2015-04-24
Thank you very much. The information you've pointed is truly clear and allow me to insert my mods.

For the records, the tty conf file is unique now: [FONT=courier new]/lib/systemd/system/getty@.service[/FONT]

---

