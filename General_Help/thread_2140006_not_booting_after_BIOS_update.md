---
title: "not booting after BIOS update"
date: 2013-04-28
forum: General Help
---

### Post by Meshal-USA on 2013-04-28
hi, i'm having a really big issue and hoping if you could help me solve it.

i have a laptop and have installed ubuntu and windows 7 on it. today when i was working on windows i got a message stating that i need to update BIOS. the update went smoothly but when i restarted the laptop i'm stuck with black screen and it doesn't boot up. i tried everything. i tried the simple stuff at first but it didn't solve it. then i tried phoenix BIOS to reset the BIOS and that also did not work with me. and then i removed the cmos battery hoping that will reset the BIOS but also with no luck at all :(

i'm really hoping if you could help me solve this issue.

looking forward to your respond, thanks in advanced.

---

### Post by zero2xiii on 2013-04-28
Hay,

Can you get to the POST screen at all?

Does the laptop start up, and are you able to enter the BIOS, or does the screen not activate at all during powering on?

What brand of laptop is it? Product code? Are there any markings on the motherboard you could see that could help us identify the board used and possible debug setups?

Kind regards

---

### Post by oldfred on 2013-04-28
Had you made any settings changes in BIOS. Often you have to change from IDE to AHCI, or turn on settings to use USB keyboard & mouse. 
Installing a BIOS resets all those settings to defaults, and a new BIOS may not even have the same defaults.

After my last BIOS update and many hassles rediscovering my settings, I used camera and took photos of every screen as my backup.

---

### Post by pqwoerituytrueiwoq on 2013-04-28
Did the BIOS update add 'secure boot' cause that could cause a problem, to fix that go into the bios and turn that off

---

### Post by Yellow Pasque on 2013-04-28
First, try a hard reset. Not only do you need to remove the battery, but you need to hold the power button for 15 seconds: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01684768&tmp_task=solveCategory&cc=us&dlc=en&lc=en&product=5193775](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01684768&tmp_task=solveCategory&cc=us&dlc=en&lc=en&product=5193775)

Next, try to retrieve the previous BIOS:
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02693833&tmp_task=solveCategory&cc=us&dlc=en&lc=en&product=5193775](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02693833&tmp_task=solveCategory&cc=us&dlc=en&lc=en&product=5193775)

---

