---
title: "Connect HP Deskjet 3733 All in One Wireless Inkjet Printer to Ubuntu Workstation"
date: 2019-01-07
forum: General Help
---

### Post by ahounsome on 2019-01-07
Hi Guys,
I've my Dad a new printer to replace his aging Desk jet 960. This printer was attached via serial cable and was working fine and the Linux printer software has been doing it's job for years. So now I've hooked up an HP 3733 with a usb to printer cable and the printer icon appeared as expected with a big green tick next to it. Unfortunately it doesn't work. I can open up the print dialogue box and it tells me its rendered but goes no further. When I set up the printer I got the usual drop down menu asking me to choose the make and model. The exact model wasn't there but it recommended one (so I picked this). Anyone any ideas?
Thanks
Andy

---

### Post by Ralph L on 2019-01-07
Don't know if this will help, but I always install hp printers under Terminal using ```
hp-setup -i 10.0.0.15

```  "10.0.0.15" is my printer wifi address.  You would need to change it to your printer wifi address.

---

### Post by MoebusNet on 2019-01-10
Have you tried the *hplip* application? It should be available through your software repository. If Ubuntu's version isn't working for your printer (ie, brand-new printer model) then you can download it from the HP Support website: [https://developers.hp.com/hp-linux-imaging-and-printing](https://developers.hp.com/hp-linux-imaging-and-printing)
BTW, unless you are connecting via WiFi, you shouldn't need its' WiFi address. A USB connection should mount & set up automagically. I always get my printers working on USB first, then worry about WiFi (if available).

---

