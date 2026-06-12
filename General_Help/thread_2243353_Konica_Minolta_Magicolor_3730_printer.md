---
title: "Konica Minolta Magicolor 3730 printer"
date: 2014-09-08
forum: General Help
---

### Post by lockhands on 2014-09-08
I have an old PC Intel 4 - 3.0 ghtz that has run for several years on XP without any problem. I have managed to get it going with a dual boot into Ubuntu 12.04 LTS, but I cannot update it to a later OS as I am informed the Graphics card will not support it (Gallium 0.4). Having said that, it otherwise seems to work fairly well except that I cannot get my Komica Minolta Magicolor 3730 printer to function over my Network (wired  Ethernet (eth0) connection). It talks to the Printer, but prints only blank pages.

Help please.

lockhands.

---

### Post by buzzingrobot on 2014-09-08
Consider an Ubuntu flavor -- Lubuntu or Xubuntu, for example -- that do place as many demands on the video card. (Specificlly, don't require 3D compositors.)  You can boot live images to check them out.

If the printer works when directly attached to the machine, then you've isolated the blank page problem as a network issue.  If it doesn't work when directly attached, it's possible that it requires a proprietary driver -- a good number do -- that the vendor does not allow to be hosted on Linux repositories.  A Google search on your specific printer model would be a place to start.

---

### Post by MrSteve on 2014-09-08
this maybe of help its a postscript printer driver for linux

[http://www.openprinting.org/driver/Postscript-KONICA_MINOLTA/](http://www.openprinting.org/driver/Postscript-KONICA_MINOLTA/)

you will need the DEB download and then right click the file and use the software centre to install
believe me it took some hunting down  ...

---

### Post by lockhands on 2014-09-09
Thanks MrSteve,

Yes have managed to install the PPD, but please excuse my ignorance, what the hell do I do now?
As you will know Konica will not offer any support for their printers running on Linux/Ubuntu, and unfortunately setting up a Postcript Printer in Ubuntu is not quite as simple as with XP. In the first place if you try to find it on the Network using the "ip address" it does not do so.

I really appreciate your help.

Cheers,

Lockhands.

---

### Post by MrSteve on 2014-09-09
use the add printer setup to add the printer using the PPD
find out the IP address from the router for the printer then add that address to the printer setup 
something like this within connection setup ... socket://192.168.1.4:9100

---

### Post by lockhands on 2014-09-10
Thanks again MrSteve,

I have attached a screen shot of the .ppd files which you suggested I save to my System (See attached Screen Shot), but I cannot see any there that relate to my Magicolor 3730 Printer. I have tried several of them, but none of those worked.
Any other ideas?

Thanks again for your interest.

Cheers,

Lockhands.

---

### Post by rbmorse on 2014-09-10
I just pulled the specs on the printer and I don't see any mention of Postscript support. [http://kmbs.konicaminolta.us/wps/wcm/connect/84001987-f6ba-4c0f-b37a-3e8d8c9cab4a/magicolor_3730DN_Spec_Sheet.pdf?MOD=AJPERES&CONVERT_TO=url&CACHEID=84001987-f6ba-4c0f-b37a-3e8d8c9cab4a](http://kmbs.konicaminolta.us/wps/wcm/connect/84001987-f6ba-4c0f-b37a-3e8d8c9cab4a/magicolor_3730DN_Spec_Sheet.pdf?MOD=AJPERES&CONVERT_TO=url&CACHEID=84001987-f6ba-4c0f-b37a-3e8d8c9cab4a)

The only thing it mentions is "host-based GDI" and I'm pretty sure that means the printer off-loads some processing to the host computer's operating system.  We used to call these a "Winprinter", but this one looks like it has support under OS X as well.  

Unless Konica makes a Linux GDI for this printer, I doubt you'll be able to use it on a Linux host.

---

### Post by buzzingrobot on 2014-09-10
For the OP:  'GDI' is 'Graphic Device Interface', an older Windows approach to enabling applications to create displays for screens and printers.  Konica was cutting costs here by offloading some of the printer's function to the GDI code within Windows.

---

### Post by MrSteve on 2014-09-10
looks like we maybe out of luck with that PPD

not sure if gutenprint will work but heres a link to sourceforge
[http://sourceforge.net/projects/gimp-print/?source=directory](http://sourceforge.net/projects/gimp-print/?source=directory) 

after this im out of ideas ...

---

### Post by lockhands on 2014-09-15
Dear MrSteve,

Thanks again for your efforts and those of your colleges also.
I rather suspected this was going to be outcome. 
It still mystifies me as when I contacted Minolta they confirmed that there was no Printer Driver made for use on Linux/Ubuntu OS's but did suggest following a instruction leaflet put out by Epson (copy of relevant pages attached), which I found a bit wierd but tried to go along with the idea using their instructions for "Non Postcript" printers using either "GhostScript" and or "Cups", but as you will already realize, I am not that familier with Ubuntu OS and am still learning how to install new applications which has lead to complications. 

I had hoped that using "GhostScript" would not necistate having a PostScript or existing "Windows" Printer driver.
I have attached a copy of the document.
So far, I have just about given up on this excersize, but if anyone can offer any other method of overcomming this problem, I would be most grateful.

Thanks again.

Lockhands

---

