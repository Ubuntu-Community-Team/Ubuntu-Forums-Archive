---
title: "cant print to remote printer after 7.10 upgrade"
date: 2007-12-21
forum: General Help
---

### Post by svref on 2007-12-21
7.10 has killed this computer's ability to print to a cups printer on a debian host. Probably its just a missing line in some /etc/cups file.

In /etc/cups/client.conf we have:
  ServerName wifihome
(this survived the upgrade intact)


In /etc/cups/cupsd.conf I added in desperation
  Listen wifihome:631  # <-- added desperately!
  Listen localhost:631
  Listen /var/run/cups/cups.sock

Now the printer doesn't show up in any print dialog, and System > Administration > Printing brings up a dialog called "Printer configuration - wifihome", which is odd because "wifihome" is the hostname of the computer that's got the printer plugged into it, not this client computer.  Also, everything in the dialog is greyed out, including "New Printer".

It worked in Feisty...I wonder what changed?

---

