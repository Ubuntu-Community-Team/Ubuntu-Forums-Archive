---
title: "Epson printer support"
date: 2017-09-13
forum: General Help
---

### Post by kwalters on 2017-09-13
I run an AMD Athlon 84 (4200 X 2) which I dual boot between Ubuntu 16.04 and Windows 10. My printer is a networked Epson XP412.  I see from my earlier posts that I have been using that same combination (albeit with Ubuntu 15.04) since at least 29 Oct 2015.

Having lost the use of my hard disk, I did a clean install of 16.04 about 3 days ago.  i attempted to install the printer drivers through the ubuntu OS using the system settings icon.  The system identified my printer as a network asset and started to install the driver.  The driver file was a "Seiko Epson" offering  with 201301 in its title (as have the previous ones).  But this one got half way through the installation and then froze the PC completely; I tried that 3 times with no success.

I then went to the Epson UK support page, which identified my OS as  Linux and announced that they do not do drivers for that OS.  Offered an on line chat i accepted and was told that they do not do Linux drivers.  i explained that I had been using one of theirs for this printer for some years got me nowhere.  That particular exchange did for Epson customer support what The Boston Strangler did for door to door salesmen.

Could anyone on this forum suggest how I might get this printer to work in UBUNTU.  I hate having to boot into Windows for all my printing  

Many thanks

KW

---

### Post by bcschmerker on 2017-09-13
Out at my quarters in East Contra Costa, CA, USA, I use a WF-3520 on occasion, and Seiko Epson Corporation maintains a driver and application repository at Download.EBZ.Epson.net.  The appropriate drivers can be downloaded via [/DSC/Search/01/Search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) at Download.EBZ.Epson.net.  Be advised that this Website, at last check, still had a SHA-1 certificate; Add-APT-Repository and APT-get will issue warning.  If not already installed, run:
```
sudo apt-get install alien
```
which will call up all related Depends for installation.

---

### Post by ajgreeny on 2017-09-14
Try adding the printer again using cups webmin page at [http://localhost:631/](http://localhost:631/) if this is not how you did it last time.

---

### Post by kwalters on 2017-09-14
Many thanks for those 2 replies.  However, in each case, the web site addresses come up in red and my local host refuses to go to one of them. The other, the Epson Download page does a search for  XP412 and Linux OS and comes up with zero resulis.  I am not happy about amending my firewall settings (even if I knew how to do it

KW

---

### Post by untrustytahr on 2017-09-14
If I remember correctly, when 16.04 came out there was a problem installing Epson printers.  Something about not having lsb installed because upstream debian deprecated it.  I don't know if later versions added it or not.  If you search "ubuntu 16.04 epson lsb" I'm sure you'll get a bunch of hits.  I can't vouch for the solutions as I don't use any epson printers.

---

### Post by kwalters on 2017-09-16
Many thanks Untrusty tahr. I will go away and try what you suggest
KW

---

### Post by Doug S on 2017-09-16
I have never been able to make my networked Epson work force pro (WP-4530) work with Ubuntu linux, until a couple of days ago. (I admit I didn't try very hard, because I normally print from widows computers. And I had dependency issues when trying to install the lsb package that untrustytahr mentioned (that was a year ago))

I brought my test 17.10 VM computer up-to-date. I noticed that it was indicating that it found a new network printer, and it just worked.

---

### Post by Geoffrey_Arndt on 2017-09-17
Did you try OpenPrinting.org?  (note the deb file . . install via "gdebi")

[http://www.openprinting.org/printer/Epson/Epson-XP-412_413_415_Series](http://www.openprinting.org/printer/Epson/Epson-XP-412_413_415_Series)

---

### Post by kwalters on 2017-09-17
SOLVED AT LAST!

Many thanks to all those who replied.

After much trawling through old Forum posts, I finally found a simple answer. It involved installing a new program as follows:

sudo apt-get install printer-driver-escpr

Then I returned to the system settings icon and added the printer again.  This time it worked and I have managed to use it on the machine to which it was connected via USB and on another machine which used it as a network printer.  Incidentally, the driver that was installed by this process was the one with 201301 in its title. And it was issued by SEIKO EPSON (whose customer support staff appear never to have heard of it)  I refer their customer support staff to St Matthew, Chapter 6 Verse 3:  "...let not thy right hand know what thy left hand doeth."

My next project will be to see if I can get XSane and Simple Scan to work on the machine.  That will, however, have to wait until the Ubuntu Software Centre starts to work in this new (to me) 16.04 version; at present, it takes me to the first page of the USC for exactlly 3 Seconds, then leaves.  So I cannot install either program.

KW

---

### Post by mörgæs on 2017-09-17
Good, please mark the thread 'solved'.

---

### Post by bcschmerker on 2017-09-18
> **kwalters said:**
> SOLVED AT LAST!

Many thanks to all those who replied.

After much trawling through old Forum posts, I finally found a simple answer. It involved installing a new program as follows:

sudo apt-get install printer-driver-escpr

Then I returned to the system settings icon and added the printer again.  This time it worked and I have managed to use it on the machine to which it was connected via USB and on another machine which used it as a network printer.  Incidentally, the driver that was installed by this process was the one with 201301 in its title. And it was issued by SEIKO EPSON (whose customer support staff appear never to have heard of it)  I refer their customer support staff to St Matthew, Chapter 6 Verse 3:  "...let not thy right hand know what thy left hand doeth."

My next project will be to see if I can get XSane and Simple Scan to work on the machine.  That will, however, have to wait until the Ubuntu Software Centre starts to work in this new (to me) 16.04 version; at present, it takes me to the first page of the USC for exactlly 3 Seconds, then leaves.  So I cannot install either program.

KW
**Congratulations on an alternate route to a working driver.**  Driver epson-inkjet-printer-201301w is built for the XP-400 Series.  I've epson-inkjet-printer-201212w for the WF-3520; each of the XP, WF, WP, and Stylus models currently supported has a driver available, which the Epson ESCP/R installer will call up as appropriate from Download.EBZ.Epson.net.

---

