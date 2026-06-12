---
title: "[SOLVED] Printer suddenly stopped working - Kubuntu Dapper"
date: 2007-10-09
forum: General Help
---

### Post by s13_mills on 2007-10-09
Hi there,

This evening I encountered a strange problem with my printer - the printer appeared "stopped" and will not restart.

Inside the localhost:631 cups manager, the error I get is:
/usr/lib/cups/backend/usb failed

I tried restarting the print server, but still no dice. I have never had any problems with this before, and as such am at a loss for what to do!

There are 2 printers on the server, one is a Brother HL2040 and the other is a raw print queue. The raw print queue is so I can print on the printer from my other PC which runs windows.

Any help is greatly appreciated, thanks in advance!

---

### Post by s13_mills on 2007-10-09
Have read a few articles found on google about people having a similar problem with other distros - all seem to be after an upgrade... I did recently do an update via adept updater, including a kernel update to the 2.6.15-28-386 kernel - does this help at all?

---

### Post by s13_mills on 2007-10-09
Problem solved. Reinstallation of cupsys through adept, followed by starting the printers through the cups web interface fixed the problem straight away. Best of all, there was no need to reinstall the printer drivers.

---

