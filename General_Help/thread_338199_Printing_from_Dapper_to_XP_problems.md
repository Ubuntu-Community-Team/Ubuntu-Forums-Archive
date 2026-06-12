---
title: "Printing from Dapper to XP problems"
date: 2007-01-14
forum: General Help
---

### Post by VoodooSteve on 2007-01-14
For a while now I have been trying to setup a shared xp printer on my Dapper system. Unfortunately, I get very, very close to success and the document does not print.

I have installed Samba and can connect to my XP shared folders. However, Windows Network under Network Servers shows nothing. Using the New Printer wizard, I select Windows Printer, put in the IP address of XP machine, and the name of my printer. I select my driver (HP PSC-1300) and finish the wizard.

I try printing a document and the printing spool on my XP computer shows the document as printing. The Job viewer on the Ubuntu computer shows nothing and the printer makes some noise but nothing happens. The Print Spool on XP freezes up  and I have to reboot the computer to clear it.

Any ideas on how I could get my printer to work?

---

### Post by NewbornPenguin on 2007-02-10
Hi. This is my first post and I hope it can be helpful. I was dealing with the same issue. My printer (HP 1310) was making noise but nothing else. You may want to try the **Deskjet 3420** driver instead of the psc 1300. I know it sounds weird but HP suggests it and it is the only one I got to work properly. Also, **make SURE  to disable bi-directional printing **on the XP machine. After that, everything prints as it should.Hope this is some help.

---

