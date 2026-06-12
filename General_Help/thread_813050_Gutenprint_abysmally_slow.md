---
title: "Gutenprint abysmally slow"
date: 2008-05-30
forum: General Help
---

### Post by Zyrshnikashnu on 2008-05-30
I recently installed Xubuntu 8.04 on my parents' desktop because Windows had slowed the computer to a crawl. Xubuntu works great so far, as expected, but printing is giving me problems.

I have an Epson Stylus Color 400 and I'm using the [recommended](http://linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Color_400) Gutenprint 5.02 driver with CUPS, but printing on standard quality is absurdly slow. It takes at least 20 minutes to print a page of text! Lower qualities are faster, but the quality is horrible.

I also tried using the stcolor driver, but it acts much like Gutenprint on low quality: fast, but poor.

Is there a driver or setting I can use that will make printing bearable?

---

### Post by plucky on 2008-05-30
> Is there a driver or setting I can use that will make printing bearable?


When you install the printer,do not accept the recommended Gutenprint driver ,but go and search for drivers and you will find one under Epson for the stylus color 400.I use the driver for Epson Stylus color 900 on Xubuntu 8.04 on a p3 600 Mhz with 128M of memory and it is not too bad for printing speed.


Good Luck

---

### Post by Zyrshnikashnu on 2008-05-30
> go and search for drivers and you will find one under Epson for the stylus color 400.

I don't think I understand. When installing the printer, I have four driver choices under Stylus Color 400:

CUPS+Gutenprint v5.0.2 Simplified
CUPS+Gutenprint v5.0.2
Foomatic/mj6000c
Foomatic/stcolor

None of these drivers are acceptable. mj6000c only prints black masses, stcolor has poor quality, and Gutenprint is too slow to be practical. There are no other options that I can see.

---

### Post by PeterBBB on 2010-03-31
I have the same printer and had the same problem. It looks to me that the resolutions used are inappropriate for this printer, which only has 180x180, 360x360 & 720x720. 

This worked for me, using version 5.2.5
Edit the ppd file you are using, start with a Gutenprint simplified. Make sure 'text' and rgb color are selected in printer options first. The file will be in /etc/cups/ppd
You need 'sudo' etc to be able to save changes. Find the block of lines starting with *stpquality and try replace them with this lot

```

*StpQuality None/180dpi (2):	"<</HWResolution[180 180]/cupsRowFeed 2>>setpagedevice"
*StpQuality FastEconomy/180dpi (3):	"<</HWResolution[180 180]/cupsRowFeed 3>>setpagedevice"
*StpQuality Economy/180dpi (4):	"<</HWResolution[180 180]/cupsRowFeed 4>>setpagedevice"
*StpQuality Draft/360dpi (3):	"<</HWResolution[360 360]/cupsRowFeed 3>>setpagedevice"
*StpQuality Standard/360dpi (4):	"<</HWResolution[360 360]/cupsRowFeed 4>>setpagedevice"
*StpQuality High/360dpi (5):	"<</HWResolution[360 360]/cupsRowFeed 5>>setpagedevice"
*StpQuality Best/720dpi (4):	"<</HWResolution[720 720]/cupsRowFeed 4>>setpagedevice"
*StpQuality Best1/720dpi (5):	"<</HWResolution[720 720]/cupsRowFeed 5>>setpagedevice"
*StpQuality Best2/720dpi (6):	"<</HWResolution[720 720]/cupsRowFeed 6>>setpagedevice"

```


The sweet spot for speed/quality text seems to be around RowFeed 3 or 4, at 180 or 360 dpi. 
Its not as good as in Windows yet, but it seems much better than it was.

---

