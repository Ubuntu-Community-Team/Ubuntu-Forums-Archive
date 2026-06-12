---
title: "HP OfficeJet 4200, cant add from other computer.  Both on Hardy Heron."
date: 2008-05-22
forum: General Help
---

### Post by herbie643 on 2008-05-22
I have 2 computers.  HP OfficeJet 4200 on one.  On Gutsy when i  added it on the other computer it worked fine.  Now, Im on Hardy Heron and it only works on the computer its attached to.  Its USB.  I have tried everything and nothing seems to work.  Im new to Ubuntu but not all that new to Unix, worked on SCO,AIX some time back.  So I can navigate reasonably well.  I have added the one computer trying to access the printer in   hosts.allow.    that didnt do it.  Any ideas, anyone?

---

### Post by herbie643 on 2008-05-23
Doesnt anyone have an idea?

---

### Post by plucky on 2008-05-24
> Doesnt anyone have an idea? 


Have you enabled sharing of the printer?

**System > Administration > Printing > Server Settings**

And tick the shared printer box.You might have to reboot the machine the printer is connected to for it to be seen on the network.

Then on the other machine,under server settings,tick the box that says **Show printers shared by other systems**.That was all I had to do with Hardy.

Good Luck

---

### Post by herbie643 on 2008-05-24
Plucky,
That did it.  Thanks so much.  It really was a DOH !   I should have thought of that myself.  
Thanks again

---

