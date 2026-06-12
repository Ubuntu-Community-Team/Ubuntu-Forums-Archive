---
title: "HP scanner stops working"
date: 2007-01-28
forum: General Help
---

### Post by srunni on 2007-01-28
Hi,

I've got a HP PSC 1510 all-in-one printer/scanner/copier. I've used xsane with it for a long time, but a few days ago, it just stopped working. Now when I scan something, I get just a small rectangle at the corner of the scanned document, instead of the whole thing. Was there an update to the driver or xsane recently? Because I didn't touch the settings at all.

Thanks in advance for the help!!

---

### Post by srunni on 2007-01-29
Update: still doesn't work with xsane, but works great with kooka. I'm guessing something in a recent xsane update broke the compatibility or something. Anyway, doesn't matter to me now, but the xsane folks might want to take a look at the compatibility with the HP PSC series with their latest version of xsane.

---

### Post by myke on 2007-02-16
After the most recent linux kernel upgrade, I can't get xsane nor kooka to launch!  They both crash whether my scanner is even hooked up or not now.  No one seems to know how to help me with this and I feel quite lost on the matter.

Update:   for some reason, a setting with my samsung printer was affected but I found a solution that changed the setting and now my scanner software is working again.  Oddly ... though the setting was relative to my printer, the printer itself never stopped working!  

The solution I found::

For some reason ... & I don't know why ... after the kernel upgrade, it apprantly affected a setting with my Samsung printer which in turn affected the scanner software even though the printer never stopped working.   After poking around the forums a while, I found this thread:

[http://www.ubuntuforums.org/showthread.php?p=2167697#post2167697]("http://www.ubuntuforums.org/showthread.php?p=2167697#post2167697")

I used the chmod solution and commenting out one line in a root file and now both kooka & xsane are working again.

Specifically, this is what was suggested and what fixed my problem & hey ... I don't know what the kernel upgrade had to do with it but I'm just glad the solution turned out to be relatively simple:

you'll find xsane now executes as root. (This is also true if you have a multifunction printer, but see below instead of this step.) To fix this, since you don't want to run xsane as root, do the following:
a: in a terminal, type "sudo chmod -s /usr/bin/xsane"
b: sudo edit /etc/sane.d/dll.conf, and comment out (add a "#") in front of the line that says "smfp" (probably the last line).
If you only do (a) and not (b), xsane will crash.

Good luck, and let me know if you have success and/or failure, and I'll try to modify accordingly.

---

