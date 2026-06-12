---
title: "printing from windows via samba does not work anymore"
date: 2013-06-07
forum: General Help
---

### Post by stephan0h on 2013-06-07
It used to work without problems that my wife printed her stuff from her windows pc to the printer connected to my ubuntu pc. But now this does not work anymore, the print jobs just hang on windows. Printing works ok on Linux.

The printers section in smb.conf looks like this:

[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   read only = yes
   create mask = 0700
   public = yes
   use client driver = Yes

I have upgraded the system to the latest of ubuntu recently - and I think we didn't print from windows since then. Maybe there lies the problem?

Any help please!

Thanks,
Stephan

---

### Post by ahallubuntu on 2013-06-07
~

---

