---
title: "Epson CX6000 - prints only blank pages"
date: 2006-11-24
forum: General Help
---

### Post by cmost on 2006-11-24
Hi guys & gals.  I'm hoping someone with more expertise than I apparently have can help me troubleshoot my new Epson Stylus CX6000 multi-function printer.  I installed the printer according to the instructions and it prints fine when attempting to make copies from the flatbed (meaning ink, paper feed, etc. working properly.)  Ubuntu immediately recognized the printer as a Stylus CX6300 and I went through the Wizard to install the new printer choosing the gutenprint driver that was recommended.  Also, the printer's on-board flash storage slots were picked up and are showing in computer:///.  Unfortunately, when I try to print anything, the printer just spits out many blank pages and I have to unplug the printer to get it to stop.  What could be the problem?  According to LinuxPrinting.org, this printer is supported using the Epson Stylus C84 drivers.  Switching to this driver does not solve the blank pages problem.  Any ideas?  I just bought this printer because my sister has a similar one working flawlessly under PCLOS.  I would hate to have to return it for another.  Thanks.

---

### Post by ReaderRat on 2006-11-24
I have seen a couple of posts about Epson Stylus. Some have said that you need to have the printer turned on and connected (USB) while you install the driver (unlike a windoze install) and you may have to reboot after install. I will look further into this...

---

### Post by cmost on 2006-11-24
I would really appreciate your help!  I did have the printer turned on during the install, and, I have rebooted.  I've been searching google fora solution, but I haven't found one (in English) yet.  Thanks again for helping...I look forward to your insight.  :D

---

### Post by cmost on 2006-11-25
*Bump*

---

### Post by ReaderRat on 2006-11-27
Do you have **gutenprint** loaded as the driver? Be sure all ink cartridges have ink in them (should have with a new printer). Be sure the ink cartridges are fully seated in the cartridge holder (should hear a soft "click" when installed). Be sure your printer is selected as the default printer in System >> Administration >> Printing (should have a check/tick mark in a circle above it). That's about all I can think of....maybe someone with the same problem can solve this....If you do solve it, please post the solution....BUMP...

---

### Post by cmost on 2006-11-28
"Do you have gutenprint loaded as the driver? Be sure all ink cartridges have ink in them (should have with a new printer). Be sure the ink cartridges are fully seated in the cartridge holder (should hear a soft "click" when installed). Be sure your printer is selected as the default printer in System >> Administration >> Printing (should have a check/tick mark in a circle above it)."

Thanks for you suggestions.  I did have gutenprint loaded as the driver I also made sure the printer worked flawlessly under Windows (ensuring the print cartridges were properly installed.)  The printer was also set as the default.  Unfortunately none of these suggestions would permit anything but a steady stream of blank pages.  ](*,) 

I gave up...I returned this printer to the store and exchanged it for an HP all-in-one.  I did some research and HP provides much better Linux support than Epson.  I haven't hooked up the HP printer yet, but, I hope it works well.  Thanks again for your assistance.

---

### Post by cmost on 2006-11-29
Ok, I purchased an HP PhotoSmart C5180.  This is purported to the "the fastest photo printer."  It's a multi-function printer, scanner, copier and fax machine.  It also has an on-board media card reader which accepts numerous flash memory cards.  Though no native Linux drivers ship in the package (Windows & Mac CD's only) they do fully support Linux with drivers and instructions from their web site.  I have to give HP a lot of credit.  Their printers work on Linux almost exactly as they do on Windows or Mac, with a feature-rich GUI interface for monitoring printer status, ink levels, etc.  With the HP sponsored HPLIP project ([http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)) most HP printers are fully supported natively on Linux and new models are added about two weeks after HP releases them.  I wish other hardware vendors would take a cue from HP.  HP has my business from now on.  Way to go HP!

---

### Post by tabinin on 2006-12-05
I just wanted to add that I bought this printer and had it printing in a few minues (in color) under Kubuntu Edgy.  I used the CX5800 driver in the KDE printer settings (with gutenprint).  The scanner was not detected and it looks like I might have to install iscan to make it work.

---

### Post by raffiki on 2007-05-07
Yep I have the CX6000, and used the CX5800 driver.

---

### Post by larytet on 2008-01-27
same problem CX3900
Printer works fine with WinXP

Here is the story.
And printer used to work just a week ago with Ubuntu. My mum did something in the Linux (i installed Ubuntu machine for her) and the printer is gone. When i arrived i did not find Epson icon in the printers window. I connected the printer, installed CX3800 and tried to print test page. All i got was a apparently infinite number of blank pages. On one of the pages (second page) printer printed two very thin lines. After that printer continues to crank blank pages until i turn it OFF

---

