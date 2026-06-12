---
title: "trying to connect printer to pc via ethernet"
date: 2013-10-17
forum: General Help
---

### Post by vap1485 on 2013-10-17
Greetings. I just bought a Brother DCP-7065DN
It has usb & ethernet ports. I want to know, if it's possible, how to connect this printer to my PC through the ethernet port.
Is it possible? If so how?

---

### Post by leclerc65 on 2013-10-17
I have exactly the same model, but I connect it to my router.
You can have a read here
[http://ubuntuforums.org/showthread.php?t=2039840](http://ubuntuforums.org/showthread.php?t=2039840)

or try my resumé

Install    cupswrapperDCP7065DN-2.0.4-2.i386.deb
	 & dcp7065dnlpr-2.1.0-1.i386.deb
 (download from Brother.com)

In browser type
	localhost:631
	Add New printer
	Wait a while the Brother(s) will be detected, choose #2 (Ubuntu 12.04)
	Click "Share" , Supply the PPD	(Brother-DCP-7065DN.ppd)
I don't know how & where I got the PPD, but try using the 7065DN CUPS driver option first...if it works out for you, fine.

---

