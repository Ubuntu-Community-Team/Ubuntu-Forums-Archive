---
title: "Linux based RIP (Raster Image Processor)"
date: 2005-09-29
forum: General Help
---

### Post by sitedesign on 2005-09-29
Is there a way of using a Ubuntu system as a RIP.

I have a client that has just been quoted by Xerox £11500 for a Fiery EX12 
Raster Image Processor

the system is only a PIII-500 with 256MB RAM and a 9GB HDD so I am thinking 
of putting together a nice hefty system and use Ubuntu instead.

Apparently the rip just takes a PDF file then converts it to a Post Script 
file and sends it to the printer. Surely there is something on Linux to do 
this.


Any help or advice/experiences appreciated.

-- 


Regards
Peter King

[www.sitedesign.net](www.sitedesign.net)

---

### Post by Hairy_Palms on 2005-09-29
fookin hell thats a steep price!! afaik theres a program called pstopdf that you can google for, might even be in repos if your lucky then its just a matter of sending the pdf to the printer via CUPS

---

### Post by sitedesign on 2005-09-29
Cheers for the reply.

Ahh so there is.

[http://linux.math.tifr.res.in/manuals/man/pdftops.html](http://linux.math.tifr.res.in/manuals/man/pdftops.html)

pdftops seems to be just the job. Now need to look into the other functions that those RIP's do like colour calibration etc. Not sure if that is just something that they run on the printer though.

I will go vist the client and take a look then test out an Ubuntu box to see if it works as they want.

---

### Post by mcduck on 2005-09-29
As far as I know, colour profiles are something that Linux is still missing. That's not so serious when working with web graphics, but for print material this is a big problem.

Pretty nice price for a P3, anyway. The machine itself is propably worth like 20€  :D If you find a soulution, I think I'll start selling such machines ;)

---

