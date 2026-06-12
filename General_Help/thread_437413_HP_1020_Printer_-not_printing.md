---
title: "HP 1020 Printer -not printing"
date: 2007-05-08
forum: General Help
---

### Post by soho2014 on 2007-05-08
I'm wondering if someone can suggest a few things to try.  My computer detected my printer fine, and I made it default.  It knows it by name, but when I try to get it to print, nothing happens.

I'm at a loss as to what to try next?

---

### Post by fragos on 2007-05-08
Try running System-> Preferences-> HPLIP Tollbox.  If it doesn't see your printer, use the Devic e drop down menu and "Setup new device."  This is a very handy package that can even tell you the level of ink or toner.

---

### Post by soho2014 on 2007-05-08
I found out that there was a mistake in the firmware. 

I went to: [http://linuxdesktopsoftware.com/](http://linuxdesktopsoftware.com/)

and I followed the instructions very carefully, even though I don't know anything about Linux, but I copied and pasted, correcting xx with 00 for my model 1020 instead of 10xx, and it worked.

At first it didn't work because I didn't follow one of the steps which was to power down and power up the printer.  But now it all works great.

Thanks to everyone for their help.:guitar:

---

