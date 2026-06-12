---
title: "Printing - Epson @F-2540"
date: 2012-11-11
forum: General Help
---

### Post by ddjolley on 2012-11-11
I am trying out an Epson WF-2540 all-in-one printer/fax/scanner. I haven't had a lot of luck finding the correct printer driver.  I did get it to work somewhat by using a driver for a lower-numbered device in the WF series.  The 2540 has some features that I would really like to have.  So, my question is this:  Am I going to somehow be able to get a usable printer driver for the 2540; or, am I going to need to return it?  Thanks for any input.

     ... doug

---

### Post by pdc on 2012-11-14
go here Doug

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

if you click on a bit, you get to here

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18783&DSCCHK=4ef4d5c29c91ff6c711c196da42d431d2515a5ff](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18783&DSCCHK=4ef4d5c29c91ff6c711c196da42d431d2515a5ff)

as ubuntu uses debian packages, you need either the 32bit or 64bit

[COLOR="Green"]epson-inkjet-printer-201211w_1.0.0-1lsb3.2_i386.deb[/COLOR]
or 
[COLOR="Green"]epson-inkjet-printer-201211w_1.0.0-1lsb3.2_amd64.deb[/COLOR]

if you click to download, gdebi installer should jump in and offer to install: let it .........that should get you going ............

.......see how you go............post back if you need more help

...... you can see there is also a scanner driver.............

---

### Post by jmdh01 on 2013-06-29
I have just installed a WF-2540 on Kubuntu sucessfully after a lot of trial and error. The path to my successful attempt was as follows:
(1) use synaptic (or similar to ensure that you have the latest lsb and lsb-printing packages then exit synaptic (or whatever).
(2) download the driver package from Epson as described above and install it using dpkg -i [COLOR=Green]epson-inkjet-printer-201211w_1.0.0-1lsb3.2_i386.deb[/COLOR]
(3) cd to /opt/epson-inkjet-printer-201211w/ppds/Epson/
(4) gunzip -c Epson-WF-2540_Series-epson-driver.ppd.gz > Epson-WF-2540_Series-epson-driver.ppd
(5) cd /usr/share/ppd/custom ; ln -s /opt/epson-inkjet-printer-20211w/ppds/Epson/Epson-WF-2540_Series-epson-driver.ppd epson_wf2540.ppd
The the printer configuration utility will see it. I used a soft link so that i would not have to completely re do everything after a software upgrade.

I hope that this step by step description will help other plodders like me. (I have not tried the scanning function yet).

---

