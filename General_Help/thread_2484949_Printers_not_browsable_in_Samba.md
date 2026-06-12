---
title: "Printers not browsable in Samba"
date: 2023-03-15
forum: General Help
---

### Post by evaristorocha on 2023-03-15
Printers not browsable in Samba

---

### Post by evaristorocha on 2023-03-15
The output of the testparm command looks like this:
[printers]
browseable = No
comment = Printer Sharing
path = /var/spool/samba
printable = Yes


But in the configuration file it looks like this:
[printers]
comment = Printer Sharing
path = /var/spool/samba
printable = yes
;guest ok = no
;read only = yes
;create mask = 0700
browseable = Yes


This problem prevents the display of printers installed in cups, can someone help me with this? OS Version: Ubuntu 22.04.2 Samba Version-4.15.13

---

### Post by SeijiSensei on 2023-03-15
Dumb, but sometimes useful question. Did you restart Samba after making the changes?

---

### Post by evaristorocha on 2023-03-15
It was the first thing I did, however the printers only appear if I run smbcontrol all reload-config.

---

