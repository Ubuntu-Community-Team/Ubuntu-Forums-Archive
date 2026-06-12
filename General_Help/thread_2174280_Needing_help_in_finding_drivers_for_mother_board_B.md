---
title: "Needing help in finding drivers for mother board Biostar N68S3+ and updating drivers"
date: 2013-09-13
forum: General Help
---

### Post by nobody6 on 2013-09-13
Dear community

I am needing help in finding drivers for mother board Biostar N68S3+ and updating nvidia GEFORCE 210 drivers as I am using Ubuntu 12.04 and it is running slow and does not allow me to update drivers. My Bios is full and has no place to load my boot file. How can I solve this matter as I am very new to ubuntu. I would really appriciate it. If I have done any thing wrong let me know so I can try to fix it.

Kind regards

---

### Post by nobody6 on 2013-09-13
Dear nobody6

Yes I am needing Help.

---

### Post by Yellow Pasque on 2013-09-13
> My Bios is full
That doesn't make sense to me. You mean your /boot partition? If you've got full disk partitions, you should fix that before worrying about video drivers.
(Oh, and don't bump your thread more than once every 24 hours.)

---

### Post by grahammechanical on 2013-09-14
May I ask you a question? Have you installed Ubuntu? How well is it running?

I ask these questions because I am using a Nvidia Geforce GT220 which is a Geforce 210 with some small improvements. Ubuntu contains all the drivers you need. When we install we are asked if we want third party software installed at the same time. If we tick that box then Ubuntu will install the appropriate proprietary (in our case Nvidia) driver for our graphic card/adapter. If we do not tick that box then Ubuntu will activate the Nouveau open source video driver. Which I find acceptable, and am using now.

Likewise, when I installed Ubuntu all the necessary drivers for the motherboard were installed. The developers of Linux work hard to provide built in drivers of all kinds of motherboards. There are only two areas where we may need to find drivers after installation and that is with video adapters and wireless adapters. And we find them through a utility called Additional Drivers.

On the other hand, with Windows a manufacturer will need to provide  drivers for their hardware. They do not usually provide drivers for the  Linux operating system. This is why Linux developers have to provide the  drivers. You may be expecting Linux/Ubuntu to do things the same way as  with Windows. But we don't.

Did you run the live session to test how Ubuntu would work on your machine? Did Ubuntu load and run? Then Ubuntu detected your hardware and used the necessary drivers. Likewise, when Ubuntu installed it detected the hardware and setup appropriate drivers for the hardware. 

If you have hardware that is not working in Ubuntu you should describe that hardware and tell us the problems. May be we can help. Also explain what you mean by "My BIOS is full."

Regards.

---

### Post by Bucky Ball on 2013-09-14
*Thread moved to **General Help**.*

Welcome. Please wait 24 hours before bumping threads. Thanks. ;)

---

