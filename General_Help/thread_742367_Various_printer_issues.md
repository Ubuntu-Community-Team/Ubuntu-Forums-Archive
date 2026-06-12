---
title: "Various printer issues"
date: 2008-04-01
forum: General Help
---

### Post by jphekman on 2008-04-01
Since this is a good forum for finding other peoples' solutions to problems, I thought I'd post about my recent battle with my printer. No help required; I seem to be on top of matters at this point.

First, I bought a new computer, and upgraded to Gutsy (from Feisty) while I was at it. Discovered that the new computer did not have a parallel port (duh), so purchased parallel-to-USB cable for my parallel printer (from ATEN, UC-1284B). With this cable, printer was detected, and I could print a test page once, but in general the printer refused to print at all (jobs just stayed in the queue). After a lot of hair-pulling, I realized the problem was indeed with the cable. I purchased a second cable (from Belkin). With this one, the printer was detected as an unknown model (I had to tell CUPS which driver to use), but things ended up working. Apparently some cables are smarter than others. Buy a smart one.

However, before things worked, I had to turn off AppArmor. This is a problem various people have had, but it did confound the basic issue (cable problem).

Also, I discovered that evince wouldn't print. But Firefox would, and lpr would (and I could print PDFs through xpdf + lpr). That also confounded the issue. (I have a workaround but may, when I have some free time, try to figure out what exactly is up with evince, and if other applications are affected.)

Good luck to all you out there with similar problems, and I hope this post helps someone. I could not have solved my problem without this and other user forums.

Jessica

---

