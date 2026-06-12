---
title: "print server question"
date: 2008-04-18
forum: General Help
---

### Post by fouadk on 2008-04-18
hi everyone....

we are currently moving our servers from windows to linux....
we have around 6 servers and every server have a role(print, dns, dhcp, active directory, web and files sever) we want to migrate to linux, we know its hard on the part of active directory so we are keeping that but everything else is gonna be linux....

we are starting by our print server....

the thing is that we have two heavy duty laser printers ....on windows server 2003 this is done by few mouse clicks....

how can i setup an ubuntu print server that have two printers and that will devide the heavy load of printing jobs on both printing...can i also support quotas...we want a strict quota for users located on actice directory....this cost us around 1000$ for a print manager for windows....

can someone point me to the correct place to replace a windows print server,,,

i also need to mention that all this clients machine are win XP

please help...

thanks in advance

thanks in advance

---

### Post by HermanAB on 2008-04-18
I would keep the Windoze print server and just stop upgrading it.  A print server is a well defined task.  Firewall it properly, save a disk image on a DVD and cancel the Microsoft support contract for it and it should keep working forever.

Linux print server functions for Windows clients are done with CUPS and Samba, but applying the 2nd World War style paper rationing may be difficult.

---

### Post by fouadk on 2008-04-19
> it and it should keep working forever.

we dont want something that will probably work forever....we are migrating to linux because of it strong immunity to viruses and because its free....can you imagine a print manager for 1000$

is there is any solution for that in linux

---

### Post by pointone on 2008-04-19
[https://help.ubuntu.com/7.10/server/C/](https://help.ubuntu.com/7.10/server/C/)

[https://help.ubuntu.com/7.10/server/C/cups.html](https://help.ubuntu.com/7.10/server/C/cups.html)

[http://www.cups.org/documentation.php](http://www.cups.org/documentation.php)

---

