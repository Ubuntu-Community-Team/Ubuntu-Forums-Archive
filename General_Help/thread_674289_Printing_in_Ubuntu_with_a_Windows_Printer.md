---
title: "Printing in Ubuntu with a Windows Printer"
date: 2008-01-21
forum: General Help
---

### Post by mxrider on 2008-01-21
I have a Canon Pixma iP1800.  The printer is connected to the Windows XP box, and I would to like print from the Ubuntu machine which is upstairs.  I can access and view files on the XP machine, but it can't see me.  When I go to system-->administration-->printer I click on Windows Printer via Samba and I click browse but it only shows my computer in the work group and no the XP one.

Any help would be greatly appreciated.

---

### Post by compiledkernel on 2008-01-21
First off, is the printer shared? 

Secondly, pixma drivers are pretty lacking, I believe even sharing a Pixma across the bounds of a window network doesnt improve this status very much. I know the iP1500 series works well, im not sure if it means the same for the 1800s.

---

### Post by mxrider on 2008-01-21
Yeah, the printer is set to shared in Windows.  I had this same problem with my last printer, which was an Epson, but I gave up after a day or two without me getting it to work.  I also forgot to mention I'm using Gutsy.

---

### Post by compiledkernel on 2008-01-21
[http://www.linux-foundation.org/en/OpenPrinting](http://www.linux-foundation.org/en/OpenPrinting)

I always refer to the above source for printing issues. 

I cant find much referencing the printer your talking about.

---

### Post by mxrider on 2008-01-21
i installed the printer (I think) through the CUPS web interface, but anytime i try to start the printer it kills my localhost.  Any suggestions?

EDIT: I guess I didn't install it.  In CUPS I get this message for the printer

Backend /usr/lib/cups/backend/smb/MSHOME/192.168.1.100/CanoniP1 does not exist!

---

### Post by mxrider on 2008-01-21
I got it to work.  I forgot the colon and double slashes after "smb"  

YAY for me.  I'm just glad I finally got it.  Thanks for that website though, it pointed me out to the CUPS web interface

---

