---
title: "Printer - System-printer-config root only"
date: 2014-04-08
forum: General Help
---

### Post by sl0th on 2014-04-08
After upgrading from 12.04 to 13.10 my printer setup stopped working. I tried reinstalling (also purge) cups and system-config-printer-* .

Cups is running correctly and I can access the web interface, but system-config-printer fails to start (BAD-REQUEST). If I start system-config-printer as root no error occurs.

The same is true for the printing dialogue. If I start for instance firefox as root it shows the configured printer but printing does not work. I have no idea how to approach to fix the permissions in this case. I assume that this would also solve the printing problem.

Hope you can help me, thanks!

---

### Post by PotatoHead007 on 2014-04-08
hey :) Welcome to the forums. 
What type of printer is it? And did you have to install any extra files when you had 12.04? Something may have changed in 13.10 too( i wouldn't know, i am still on 12.04).

Here is a list of printer-manufacturers and a way of installing them both: [https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)
Hope it helps.

---

