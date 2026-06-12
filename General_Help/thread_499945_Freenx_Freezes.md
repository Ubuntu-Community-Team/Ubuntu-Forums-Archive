---
title: "Freenx Freezes"
date: 2007-07-13
forum: General Help
---

### Post by mowbray on 2007-07-13
I have got freenx working successfully on ubuntu 7.0.4 and am connecting across the internet using the nomachines nx windows xp client. It works really fast - almost seems like a local console.

However...... :-)

From time to time the console suddenly throws me out and the whole ubuntu OS locks up. I have to go to the physical machine running ubuntu and do a power off and power on to get going again.

I tried scheduling a reboot using cron to see if the machine would restart itself after such a lock up but it doesnt.

Does anyone have any ideas what is causing this. It doesnt seem to follow a pattern - once i was using Firefox, another time an email client and another time installing software.

TIA

---

### Post by geraldm on 2007-07-14
I have had similar experiences, rarely.  I have tended to suspect that some
page returned by firefox causes the problem, but I have not obtained convincing
proof.  Usually the mouse fails -- it is on USB, the keyboard also fails -- it is on PS/2.
I have both usb-uhci and usb-ohci hardware, the ohci being better, but not perfect. 
Perhaps someday I will find a way to cache all firefox pages. Then, on the next boot, 
the evidence will be available to confirm/deny my suspicion.
Gerald

---

### Post by mowbray on 2007-07-21
Thanks for the response. Anyone know of any decent alternatives that are similarly quick?

Thx

---

