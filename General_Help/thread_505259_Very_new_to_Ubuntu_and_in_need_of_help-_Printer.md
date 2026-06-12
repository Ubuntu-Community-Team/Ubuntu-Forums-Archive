---
title: "Very new to Ubuntu and in need of help- Printer"
date: 2007-07-20
forum: General Help
---

### Post by ltemby on 2007-07-20
Hi everyone
I have just finished installing Ubuntu after many years of being a windows user and I am glad I made the move, but there is one thing I cannot get to work and thats my Epson RX620 Printer, the system does not seem to recognise the USB connection, this is the only thing that is making me feel I should have stayed with windows because the printer is really important for my work, 

I am not worried about the scanner side of it just want to get the printer loaed and working, 

Could someone please help with a really easy non tech step by step guide to installing the printer, any help would be greatly appreciated

Thanks for any help
Les

---

### Post by lemmy999 on 2007-07-20
Epson printers are well supported in Ubuntu.

Go to system>Administration>printing. Click on printing and when the window opens click on "new printer" Ubuntu will then autodetect your printer and you just need to click on the driver for the printer. 

All done!

---

### Post by ltemby on 2007-07-20
Hi there
Many thanks for your reply - done all that  - the problem is that it does not recognise the printer has a usb connection, only serial
Cheers
Les

---

### Post by willbur on 2007-07-20
Hi Les

Welcome to the club! I found Ubuntu wouldn't recognise my USB Epson printer unless the printer was on and connected before I ran the install wizard. Maybe this helps?

---

### Post by rbmorse on 2007-07-20
Turn the printer on.  Open a terminal window and:

lsusb<enter>

does the printer show up on the port scan?  The resuly will be something cryptic, but should have the word "Epson" or "Epkowa" somewhere in it.  Mine looks like this:

> Bus 005 Device 003: ID 0409:013e NEC Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 03f0:3202 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  


---

### Post by laidback on 2007-07-20
Once you overcome your USB recognition problem you'll be pleased to know that the Epson Stylus Photo RX620 is listed in the database of supported printers. I'm running 7.04. You do need to have the printer switched on before it can be recognised, I've been caught with that myself. Take heart, you will overcome this temporary hiccup.

---

### Post by cotcot on 2007-07-20
The Epson RX620 is supported by gimp-print, so far no problem. 
Once you get the usb connection OK installing the printer through CUPS should be easy (I have the RX640 working).

As said above the output of lsusb with the printer switched on is important to know.

---

### Post by cotcot on 2007-07-20
Sorry, double post

---

