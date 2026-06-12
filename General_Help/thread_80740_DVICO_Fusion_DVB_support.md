---
title: "DVICO Fusion DVB support"
date: 2005-10-22
forum: General Help
---

### Post by pixelboy on 2005-10-22
Im sure I read somewhere that the DVICO Fusion DVB Digital TV cards would be supported in Breezy. Mine appears in lsmod (cx88_dvb) and in Device Manager as a Winfast (??) but ive been unable to get any joy from it in MythTV or scantv.

Have I done something wrong or do I need a patch / drivers?  Does anyone have a DVICO up and running in 5.10?

Thanks in advance.

---

### Post by wellery on 2005-10-23
As far as I know DVICO won't work DVB-T without patching. I had my card working in hoary and I was expecting it to work in breezy but apparently it doesn't. I haven't tried it yet but the plan is to see if this patch makes it work:

[http://www.ussg.iu.edu/hypermail/linux/kernel/0507.2/0368.html]("http://www.ussg.iu.edu/hypermail/linux/kernel/0507.2/0368.html")

---

### Post by pixelboy on 2005-10-23
Ahh IC.. Thanks wellery.

Im a bit of a n00b so a "how-to" would be much appreciated if you do get it going :)

---

### Post by BambooClaw on 2006-02-05
I have a Dvico Fusion Dual DVB-T and I used the following instructions to get it going under Breezy.  So far I only have the PCI tuner going, still working on the USB tuner.
[http://www.linuxtv.org/v4lwiki/index.php/How_to_build_from_CVS]("http://www.linuxtv.org/v4lwiki/index.php/How_to_build_from_CVS")

---

