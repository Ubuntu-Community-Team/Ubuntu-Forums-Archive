---
title: "PXE Boot + Symantec Ghost + Network Drives"
date: 2008-03-05
forum: General Help
---

### Post by vage on 2008-03-05
Hey guys, I am trying to get a nice system deployment setup going on here, and I almost have everything working except for one small part.  Currently, I have a Ubuntu VM hosting a DHCP, TFTP and PXE server.  Now when I boot up a client machine, it gets an IP, grabs the boot image from the TFTP server, and boots from the PXE server directly into Symantec Ghost Enterprise.  This all works perfectly fine, however, when I boot into Symantec Ghost what I would like to be able to do is have several network drives already attached that I can save disk images to, or pull disk images from.  So basically, I was wondering if anyone has a similar setup for this, and if they could help me out with this problem.

---

### Post by silverfroi on 2008-03-09
How did you setup your server? Please, I need help. Thank you!

---

### Post by AnRkey on 2008-05-23
Hi Vage,

I have loads of experience with this kind of stuff, on windows though. I would love to know how you got this far. Please do let us know in a mini howto if you will. I could then have a look and see if I could get a network share mounted as a drive for images to be stored or read to and from.

R

---

### Post by AnRkey on 2008-05-23
One idea... The guys that do "The Ultimate Boot CD" also have a SMB client built in to a DOS like boot image. You could take that image out of the ISO and extract it to see how they do it.

R

---

