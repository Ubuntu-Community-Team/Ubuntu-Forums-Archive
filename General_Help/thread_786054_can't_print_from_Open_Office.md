---
title: "can't print from Open Office"
date: 2008-05-07
forum: General Help
---

### Post by Lary Grant on 2008-05-07
I can't print from any Open Office app, but I can print from all other apps.   I tried rebooting, power-cycling the printer, etc.

I'm on Gutsy and my printer is a Brother MFC 210C.  Until now everything has been printing fine.... I haven't changed anything!

---

### Post by dingfelder on 2008-05-25
I am also having printing problems with openoffice.

If I create a new openoffice word document and I try and print, it does not print right, iven if it is simple (all it contains is the word "123") 

Specifically, I can print from firefox and can print test pages on my printer (Xerox Document Centre C250) but when I print from open office, it locks up the printer.

---

### Post by dingfelder on 2008-06-26
On further investigation, I opened the PPD file  and it was NOT the right driver, it was a Xerox Document Center c50 when I needed a Xerox Document Center c250   

As no Linux driver was listed, I downloaded a new driver for windows XP for my printer, opened the archive, located the PPD, and reinstalled it in cups.  It solves all my worries.

---

