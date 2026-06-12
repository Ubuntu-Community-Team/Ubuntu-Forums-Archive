---
title: "[SOLVED] Printer setting woes"
date: 2008-06-09
forum: General Help
---

### Post by cosborn72 on 2008-06-09
I'm having some printer issues that are just about to drive me crazy.  

I had switched the printer driver for my Lexmark T522 networked printer from generic PS to generic PCL.  It worked well, but for some reason the manual feed was set as the default and wouldn't change.  I switched back to the PS driver, but I continued having the problem.

In the (local) CUPS settings, I have it set to default, but in OpenOffice and Thunderbird it keeps setting the printer to Manual feed.  I have changed both several times through each program's printer settings, but they keep reverting back.  The main CUPS settings are correct, but the programs don't seem to be taking to them.

Any ideas?  All the other computers on the network (all XP) are not having any trouble, so I don't think it is a printer setting. I think the issue is on my computer.

Chris

---

### Post by emperor on 2008-08-13
Try setting the printer settings using this utility. Set as user; don't use sudo!
/usr/lib/openoffice/program/spadmin

---

### Post by cosborn72 on 2008-09-11
That fixed it.  Thanks!

---

