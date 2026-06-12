---
title: "CUPS...  Change buffer size?"
date: 2005-09-24
forum: General Help
---

### Post by ckrueger on 2005-09-24
I'm new to Ubuntu, and just picked up an old HP LaserJet 6P (LPT) from a client that I've decided to use as my workhorse from here on out (invoicing with an inket just doesn't feel right, especially now that I've got laser-safe letterhead), and it has been configured and everything...  However, when leaving it at 600dpi with the PostScript driver, the printer locks up and reports an error regarding a buffer overflow.  Dropping to 300dpi cures this altogether, and it can print 50+ pages at a time (that's as high as I've needed to go, thankfully).  However, I'm wondering if there's a way to change the spooler settings to make it actually spool the document (not a whole page at a time) rather than just inundate the thing with data.  I haven't cracked it open to see how much memory it can handle, but in all honesty, I'd rather just fix the spooler.  Any tips?  I was going to try foomatic-gui, however, it doesn't exactly work since it requires the gtkhtml2 library (I know Ubuntu ships with 3.6, however, for some bizarre reason foomatic-gui can only reference up to 8 character file names or some trash).  I'd appreciate any info anyone can give me.  Thanks!

---

