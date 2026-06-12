---
title: "Where does Avahi store Printer info?"
date: 2019-05-25
forum: General Help
---

### Post by markosjal on 2019-05-25
I have a printer installed in CUPS. I must use the driver from a different model to make it work. Among other things I want to see if i can manually edit what Avahi is advertising 

Avahi browse shows

Xerox_Phaser-6125 @ Hostname (correct)

Later however in Txt fields it shows "product=(DocuPrint C525 A-AP)" .......... "ty=FX DocuPrint C525 A-AP v1.0" (incorrect printer model but is the driver in use)

 I would also like to add a proper "representation" icon as is done with AirScan/eSCL scanners "representation=http://HOSTNAME./images/Icon.png" as I believe some apps will use this icon of the actual printer. 

I know that some services are in /etc/avahi/services but nothing about printers there . I figure if I can manually overwrite them then disallow write permissions, problem solved.

---

