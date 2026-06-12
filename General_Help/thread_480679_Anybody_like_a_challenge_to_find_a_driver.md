---
title: "Anybody like a challenge to find a driver?"
date: 2007-06-21
forum: General Help
---

### Post by the lemming on 2007-06-21
I'm having trouble finding a linux driver for an Epson Stylus Photo R265.

I've checked the Epson and Avasys websites
[http://www.avasys.jp/english/linux_e/dl_ink.html](http://www.avasys.jp/english/linux_e/dl_ink.html)

They say that the Avasys site has the correct driver but I can't find it.

I've even tried Mr Google but can't find anything that will work.

Maybe I'm not looking in the right place so I would be grateful if somebody could help me find the correct driver.

Cheers

---

### Post by ajgreeny on 2007-06-21
I don't know this printer but I found myself in a similar situation with a driver for an Epson stylus photo 830U printer which does not appear in the list showing from cups.  The nearest I can find is the 870 version which certainly works but I'm not sure if it has all the same options as the 830 driver did in dapper.  What has happened here?  Where did the 830 driver go to?

---

### Post by Brucevdk on 2007-06-21
I just searched around a bit and this seems to be discussed in the thread [Epson Stylus Photo R260 printer]("http://ubuntuforums.org/showpost.php?p=2647245&postcount=4").

From the site you linked, the [binary RPM package for  Stylus Photo R260/R265/R270]("http://lx2.avasys.jp/pips/lite1.0.0/pipslite-cups-1.0.0-1.i386.rpm") [avasys.jp], follow the instructions in the thread linked above to install it. The associated "source" package (also available through the site) looks to contain source code licensed under the GPL and some proprietary bits (object files).

Hope this helps you.

---

### Post by ajgreeny on 2007-06-22
As a follow-up to my post yesterday, I have just found a solution to my problem of the missing driver for my epson stylus photo 830u.  I noticed a driver database in synaptic that is not installed by default on the system called foomatic-db-gutenprint, which I installed, and guess what?  Suddenly my printer is listed in the epson list when installing a local printer, so now I'm happy and have full facilities available which were not with the previous driver; OK, it did work but with very few options for resolution of printing or paper types. etc.

If you have not got that package installed for your system, give it a try.  It might be just what you needed.

---

### Post by Gael05 on 2007-06-22
Hi...
check on [http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_R265](http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_R265) or [http://www.avasys.jp/english/linux_e/dl_ink.html](http://www.avasys.jp/english/linux_e/dl_ink.html)

---

