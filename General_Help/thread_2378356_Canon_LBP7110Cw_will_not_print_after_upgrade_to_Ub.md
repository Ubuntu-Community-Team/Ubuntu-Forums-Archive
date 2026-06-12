---
title: "Canon LBP7110Cw will not print after upgrade to Ubuntu 17.10"
date: 2017-11-22
forum: General Help
---

### Post by freddy-oprea on 2017-11-22
After upgrade to Ubuntu 17.10 my Canon printer LBP7110Cw will not print anymore (wired or wireless). Even though the system recognizes the printer, removed and reinstalled the drivers I got from Canon direct, rebooted everything as instructed, got only positive messages from Ubuntu (printer ready, printing completed, showing ink levels, etc.), not one error message, network health all right - the printer will not print. It worked perfect with Ubuntu 17.04 and now it works with Windows 10. What can be done ???
Thank you.

---

### Post by pdc on 2017-11-22
so this uses one of Canon's UFR drivers; the UFRII LT variant; [https://www.canon-europe.com/support/consumer_products/products/printers/laser/i-sensys_lbp7110cw.aspx?type=drivers&driverdetailid=tcm:13-1156622&os=Linux%20(64-bit)&language=EN](https://www.canon-europe.com/support/consumer_products/products/printers/laser/i-sensys_lbp7110cw.aspx?type=drivers&driverdetailid=tcm:13-1156622&os=Linux%20(64-bit)&language=EN)

it is called version 1.4 and was released only a short time ago; (14th Nov): would that be the driver you used?

some suggest there really should be a health warning for doing "upgrades" ....... there are quite a number of posts now with scanner; and printer issues; 

16.04 was an LTS release: long-term support; in between, Ubuntu do the sprints ........ they release short-support variants; and 17.10 was full of new stuff; not all can be warranted to be rock-solid: so users discover flaws; report them; they get fixed; and others benefit; next LTS is 18.04 and the emphasis there will be stability I understand


PS I will also ask after you answer this post that it be moved to the Hardware section; as all the printer stuff ends up there

---

### Post by freddy-oprea on 2017-11-23
Thank you. You are right, it is version 1.4 of the driver that I tried with the only result that I won't get any error messages - thus making the job of finding a solution so much harder - everything is just perfect but not printing.

---

### Post by col48 on 2017-11-23
I had something vaguely similar with a different Canon printer which was OK in 12.04 but got bad habits in 16.04 (it printed, but duplex printing and colours were unsatisfactory).  My workaround was to print from 12.04  (I have dual boot) when duplex or colour was needed, which is not often.  Then the printer developed another problem which prevented printing totally.  I decided to replace it with the same model (still available and cheap!).  To my surprise the problems disappeared.

Therefore the printer's firmware must have been changed - there is no hint on Canon's websites (or anywhere else I could find) that this had happened.  Nor had I had any response from Canon when I had asked for support.....

This involves expense and possibly will be to no avail, but if all else fails...
Hey, you could borrow one!!

---

### Post by kurt18947 on 2017-11-23
> **freddy-oprea said:**
> Thank you. You are right, it is version 1.4 of the driver that I tried with the only result that I won't get any error messages - thus making the job of finding a solution so much harder - everything is just perfect but not printing.

No help but I'm having a similar issue with a Brother scanner. The driver installs, no errors or warnings but also no scanner. I think of the interim releases as beta releases. I have 16.04 installed in another partition which is working great. If you don't need the latest kernel for hardware support, keeping an earlier functioning install is an excellent idea. I'm typing this on 17.10 and reporting any problems that arise - like the MIA scanner. I think it a low price to pay for a very good free system.

---

### Post by pdc on 2017-11-23
that is very good advice; LTS for stability; maybe run new releases on a virtual machine ....... very thoughtful

---

### Post by freddy-oprea on 2017-11-24
Thank you for your suggestion. I'm doing more or less the same thing. Working on 17.10 and printing from 17.04. However I would like to understand why this problem appeared so it won't surface in future releases. That's why I asked for help and suggestions.
Thanks anyway.

---

### Post by col48 on 2017-11-24
The essence of my post (#4 in the thread) is that the problem may be incompatibility between the driver, the 17.10 release and the printer firmware.  All three need to understand one another.  Two of the three are Canon....

---

### Post by kurt18947 on 2017-11-26
> **col48 said:**
> The essence of my post (#4 in the thread) is that the problem may be incompatibility between the driver, the 17.10 release and the printer firmware.  All three need to understand one another.  Two of the three are Canon....

Correct. I hope the various hardware manufacturers are aware of any incompatibilities between the current LTS (16.04) and the upcoming LTS (18.04) so we don't have to wait until after 18.04 is released for required hardware to be supported. I wonder if Ubuntu changed something in their hardware support when they changed from Unity to Gnome-Shell.

---

### Post by freddy-oprea on 2017-11-26
Following my inquiries I got various answers from the Canon support team but at the end of the day all lead to the same conclusion: there is no printer firmware change since 17.04 and no driver change (version 1.4 is an upgrade of 1.3 that worked with 17.04 and I tried also with 17.10 but without success). So, in my opinion there is an obvious change in the Ubuntu hardware support when they changed from Unity to Gnome-Shell. It would be really helpful to know what this change is all about.
Thank you all for your attention to this problem of mine.

---

### Post by haitem-belgacem on 2017-12-20
Hello
is there a solution for this issue since the last month?

---

