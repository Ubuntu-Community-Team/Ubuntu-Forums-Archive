---
title: "Is this a bug? partitions get unmounted when using &quot;root&quot;"
date: 2004-12-07
forum: General Help
---

### Post by arctic on 2004-12-07
hello everyone.

i created a /root account on two ubuntu-boxes (4.10 warty-warhog). once I log into the system as root (on "/" partition) and exit the session, i get back to the gdm screen. no problem there. the tricky part comes now:
i try to log in as normal user (on "/home" partition) after logging in as root and the /home partition is gone. it somehow got unmounted although no command was given by root. thus, no user-login is possible on the original /home partition until the system is rebooted. then i can log in as normal user again.

this happened EVERY time i tried going "root" and immediately afterwards "user". (i checked this for several days, did numerous reboots to verify that it is not some minor issue). 

did others have/can recreate this bug, too? if yes, i think it needs to be posted to the bugtracker.

---

### Post by arctic on 2004-12-08
you guys could at least take a look ... 4 views so far... ridiculous.

---

