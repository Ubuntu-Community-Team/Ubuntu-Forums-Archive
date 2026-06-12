---
title: "Epson GT-S50 scanner and drivers on 12.04"
date: 2013-01-15
forum: General Help
---

### Post by Idyll on 2013-01-15
I too am having problems getting this scanner to work properly.  I'm using Ubuntu 12.04 and sometimes it works but then sometimes, like now, when I try to start the software it pops up a dialog that says:

"Could not send command to scanner.  Check the scanner's status."

Usually if I turn it off and back on and then unplug and replug in the USB cord it will then begin working but not now.  This is getting really frustrating and I will probably have to restart Ubuntu to get it to work again.

Surely there is a way to get this scanner to work consistently using Ubuntu.  Does anyone have any ideas on this?

Thanks.

---

### Post by oldos2er on 2013-01-15
Post moved to its own thread. Rather than posting a new question in an old thread, create a new thread. More eyes will see it, and you're more likely to get better help more quickly.

---

### Post by pdc on 2013-01-17
Hi Idyll;

you don't mention how you are "driving" the scanner: 

Epson would say to go here

[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

and entering S50 you get to here

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

and clicking on scanner you get to here

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=20920&DSCCHK=1f66541498e19eb24ca3c111022918affda59631](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=20920&DSCCHK=1f66541498e19eb24ca3c111022918affda59631)

and scrolling down to click the [COLOR="Blue"]**ACCEPT**[/COLOR] button you get to the options

you don't say if you have 32bit: if we assume you do:

you would install

1) [COLOR="SeaGreen"]iscan-data_1.20.0-1_all.deb[/COLOR] ......must be first .....

2) [COLOR="SeaGreen"]iscan_2.29.1-5~usb0.1.ltdl7_i386.deb[/COLOR]

and then back to here

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

to click on plug-in and get to 

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=17956&DSCCHK=bca9599f01d018f5f2ef1b6287eaf2ddbc5c6d86](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=17956&DSCCHK=bca9599f01d018f5f2ef1b6287eaf2ddbc5c6d86)

click on **[COLOR="Blue"]ACCEPT[/COLOR]** and you choose [COLOR="SeaGreen"]esci-interpreter-gt-s80_0.2.1-1_i386.deb[/COLOR]

......that should get you working ............and you did all that?

---

