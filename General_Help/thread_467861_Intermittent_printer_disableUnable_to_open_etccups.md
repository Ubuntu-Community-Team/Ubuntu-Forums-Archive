---
title: "Intermittent printer disable:Unable to open etc/cups/classes.conf"
date: 2007-06-08
forum: General Help
---

### Post by fopetesl on 2007-06-08
Ubuntu 5.10 running on some test equipment.
We use only a couple of types of HP Printers, usually Deskjet 5550 & Photosmart 5650.  (hpijs driver)
99% of the time everything works just fine.
Occasionally, though, the printer becomes disabled and printing stops.  Jobs do go into the queue.
Re-enabling the printer manually restarts the printing.
Problem is that it's difficult for the end user to do this since he/she has no command line skills or switching out of a purpose GUI.

The only possible link I can find is in /var/log/cups/error_log: ".. Unable to open /etc/cups/classes.conf"
That's because classes.conf isn't there :(

Should it be there?
What effect is it having not being there?

 Any likely connection with the intermittent printer disable problem?

:? Still a Newb :?

---

