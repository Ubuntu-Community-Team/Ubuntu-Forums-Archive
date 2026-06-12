---
title: "Not starting and CAPS LOCK led blinking"
date: 2013-04-19
forum: General Help
---

### Post by knori on 2013-04-19
This morning I tuned my laptop on (acer aspire 5542 with ATI radeon HD4200) but it didn't.
After the loading screen, I had a message:
SP5100 TCO timer: mmio address 0xfec000f0 already in use
then the screen blackened and the CAPS LOCK led flashed.
I had to turn power off, as no key worked.
As I turned on again, the message was the same, and the loading screen was no more graphic, but text.
But the result was the same.
I also tried using previous kernel (I am now using 3.2.0.41, and I loaded 3.2.0.40) but nothing changed.

Up to yesterday everything was right, and, as far as I can remember, no automatical upgrade was done yesterday *for sure somethign changed these days with upgrades, but, for example, no kernel upgrade was done)

Trying with recovery mode, often the laptop freezed in some task I asked for (for example, start network services), and, as I am not so expert, cannot do anything useful...

I also tried to restart my system directly from recovery mode (resume normal boot), but it did not work.Black screen with the HD led flashing and keyboard not working at all (even lock keys).

I googled for the problem and also searched in this forum, but I noticed that most of those who had this problem however, after the message, had their system on, while all I get is a black screen.

Moreover, I am not a real expert, so I cannot read easily articles on launchpad.
I found out these results,
[http://www.google.it/#hl=it&gs_rn=9&gs_ri=psy-ab&cp=39&gs_id=30&xhr=t&q=sp5100+tco+timer+mmio+address+0xfec000f0+already+in+use&es_nrs=true&pf=p&sclient=psy-ab&oq=sp5100+tco+timer+mmio+address+0xfec000f0+already+in+use&gs_l=&pbx=1&bav=on.2,or.r_qf.&bvm=bv.45373924,d.ZWU&fp=e6d30027f1302e81&biw=1366&bih=576&bs=1](http://www.google.it/#hl=it&gs_rn=9&gs_ri=psy-ab&cp=39&gs_id=30&xhr=t&q=sp5100+tco+timer+mmio+address+0xfec000f0+already+in+use&es_nrs=true&pf=p&sclient=psy-ab&oq=sp5100+tco+timer+mmio+address+0xfec000f0+already+in+use&gs_l=&pbx=1&bav=on.2,or.r_qf.&bvm=bv.45373924,d.ZWU&fp=e6d30027f1302e81&biw=1366&bih=576&bs=1)
but I cannot solve my problem...

So I tried with liveCDs:
1- archlinux gave me a message like 
sp5100_tco: mmio allocation failed
and no graphical interface started
2-systemrescued CD somehow worked, and now I am using it to backup last data on my USB HDD, and I am writing this message. (also startx worked)
I checked my partition table and it gave a warning after analysis, saying that the size of the HD was smaller than expected...

Can you please give me a practical guide or some hint?

Thank you!

---

### Post by tgalati4 on 2013-04-19
How old is the laptop?  It sounds like a hardware problem.  Perhaps motherboard flexing or a short in the hinge that drives the screen.  I would pull the drive out, put it in a USB enclosure and hook it up to another linux machine for data recovery.  Then open up the laptop, clean the vents and tighten all of the chassis screws and inspect the hinge cable for wear.  Reseat the RAM sticks.  Run memtest from the Live CD to make sure the RAM is OK.

---

### Post by knori on 2013-04-20
After Memtest went OK, I tried to change my xorg.conf file using recovery start, changed the driver to 'ati' deactivating proprietary drivers, and now it works (even if sometimes during loading screen the old message still appears).
Here's the procedure I followed.
However, thanks...

In a root shell:

nano /etc/X11/xorg.conf

change the line :
Driver "fglrx"
to
Driver "ati"

I found out it but I have not the link, as I found it in the livecd session. sorry :(

---

