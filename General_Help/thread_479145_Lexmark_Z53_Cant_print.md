---
title: "Lexmark Z53 Cant print"
date: 2007-06-20
forum: General Help
---

### Post by bswartwout on 2007-06-20
I have a USB Lexmark Z3 printer that the OS finds and says it has a driver for and installs said driver.  However, the print test shoves a blank piece of paper through and does nothing else.  I have been to the Ubuntu support sight and tried their resolutions, and I have been to the lexmark sight and tried thier resolutions.  I have changed cable and medium of trasmission (i.e. usb and parallel printer calbes) This is my first foray into linux but I am a Windows IT professional and have nearly a 4.0 in a programming degree...HOW DIFFICULT COULD THIS BE.???  HELP!

---

### Post by orb9220 on 2007-06-20
[http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)

---

### Post by bswartwout on 2007-06-21
I followed all of the instructions and I am not getting any response now from the printer,  Whats next?

---

### Post by kanys on 2008-02-24
Got the Lexmark Z53 to work in Dapper (6.06 LTS).  Here's how I did it.  Following advice posted by the good folks on Launchpad, I

Logged on to [ftp://ftp.akl.lt/Linux/Baltix/Baltix-Ubuntu_packages/gutenprint/](ftp://ftp.akl.lt/Linux/Baltix/Baltix-Ubuntu_packages/gutenprint/)

then downloaded and installed these packages (in this order)

libgutenprint2_5.0.0-2ubuntu1_i386.deb
cupsys-driver-gutenprint_5.0.0-2ubuntu1_i386.deb

(I got some kinda message saying that older software was available in a software channel, but just clicked "OK" on that and it went away)

After this, I installed the Z53 by clicking System, Administration, then Printing, then doubleclicking on New Printer and choosing Lexmark, then Z53.  Lo and behold, it printed a test page (rather than shooting out a blank)

Just to doublecheck, I printed these notes from Text Editor (on the back of the test page, to save paper and natural resources).  Worked great!

Evidently, there's some kinda known problem with out-of-date Gutenprint drivers in Dapper that the packages above update.  Hey, it worked for me, and if it works, it's good!

---

