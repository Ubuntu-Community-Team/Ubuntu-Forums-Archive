---
title: "Just installed Multi-Function printer. How do I scan?"
date: 2007-05-01
forum: General Help
---

### Post by mjpatey on 2007-05-01
Hello, folks-

Just installed an HP OfficeJet 5610 All-In-One printer, scanner, fax, copier.  When I first plugged it in and ran System --> Administration --> Printing, it detected the printer just fine (in fact, showed 2 instances of it, and I selected the one whose title included the text "HPLIP", since it's an HP printer).

I can print to it just fine, but have no idea how to configure it to act as a scanner, copier and fax machine.  I did my homework before purchasing the unit, and this device is on the Ubuntu Hardware Compatibility List, with remarks stating that all functions perform perfectly.

I couldn't find any entries in System --> Administration that referred to the scanner or fax features (I assume the copier feature is handled entirely inside the unit itself).

Any idea how to use the other functions of this unit?

Thanks for any help you may have!

-Mark

---

### Post by qamelian on 2007-05-01
> **mjpatey said:**
> Hello, folks-

Just installed an HP OfficeJet 5610 All-In-One printer, scanner, fax, copier.  When I first plugged it in and ran System --> Administration --> Printing, it detected the printer just fine (in fact, showed 2 instances of it, and I selected the one whose title included the text "HPLIP", since it's an HP printer).

I can print to it just fine, but have no idea how to configure it to act as a scanner, copier and fax machine.  I did my homework before purchasing the unit, and this device is on the Ubuntu Hardware Compatibility List, with remarks stating that all functions perform perfectly.

I couldn't find any entries in System --> Administration that referred to the scanner or fax features (I assume the copier feature is handled entirely inside the unit itself).

Any idea how to use the other functions of this unit?

Thanks for any help you may have!

-Mark

I think for the scanner functionality, you need to use xsane. I'm not sure but I think it's installed by default and should be under Applications > Graphics.

---

### Post by mjpatey on 2007-05-01
Beautiful!  Worked like a charm.  Thanks, I've never done any scanning before.

-Mark

---

### Post by david.rahrer on 2007-05-11
Have you found that everything works on this one in Ubuntu?  I'm about to get one and am just checking, thanks!

---

### Post by mjpatey on 2007-05-11
> **david.rahrer said:**
> Have you found that everything works on this one in Ubuntu?  I'm about to get one and am just checking, thanks!
Yes!  I can print, scan, copy, fax and receive faxes.  It's great!

-Mark

---

### Post by rich.bradshaw on 2007-05-11
I use kooka...

---

### Post by finger51 on 2007-08-04
> **mjpatey said:**
> Yes!  I can print, scan, copy, fax and receive faxes.  It's great!

-Mark

I just got the same printer, I'm still trying to figure out how to fax directly from the document I'm working on. The only way I can fax at this point is to print out a copy of the document and place it in the fax feeder, then plug the numbers in on the 5610's keypad. 

Is there a way to fax *directly* using the 5610? meaning have ubuntu handle the dialing?

---

### Post by HermanAB on 2007-08-04
SANE - Scanner Access Now Easy

---

### Post by david.rahrer on 2007-08-10
Thanks for the advice, I finally picked up an HP OfficeJet 5610 for $89 at newegg.com - love it so far.  Before I dive into the fax setup, I have a question about the scan button.  I can scan easily using XSane, but I was wondering about the scan button on the printer.  When I press it, the display says it's not configured.  I set up hp-toolbox which has the configuration already set for "external scan command" to call XSane.  Just so I know, has anyone gotten this button to work, or is that just not an option when running on linux?  

If the fax works as smoothly as the rest, this seems to be a perfect Ubuntu multifunction printer.

---

### Post by HermanAB on 2007-08-10
HP has Linux drivers for all their printers and scanners, BUT they do not necessarily support all the fancy buttons.  

SANE can be configured to act as a scanner server and when you use it like that, the buttons are not necessarily useful to machines that are far away.

---

### Post by MeduZa on 2007-09-19
> **finger51 said:**
> I just got the same printer, I'm still trying to figure out how to fax directly from the document I'm working on. The only way I can fax at this point is to print out a copy of the document and place it in the fax feeder, then plug the numbers in on the 5610's keypad. 

Is there a way to fax *directly* using the 5610? meaning have ubuntu handle the dialing?

diferent printer same question I have the printer and a fax on printers panel, If I print to the printer everything is fine, but if I print to the fax noting happened, some one try to print documents to the fax?

see the attached pic!
[picture]("http://ubuntuforums.org/attachment.php?attachmentid=42716&d=1189089338")

---

### Post by samuraiCat on 2007-10-18
> **finger51 said:**
> I just got the same printer, I'm still trying to figure out how to fax directly from the document I'm working on. The only way I can fax at this point is to print out a copy of the document and place it in the fax feeder, then plug the numbers in on the 5610's keypad. 

Is there a way to fax *directly* using the 5610? meaning have ubuntu handle the dialing?

Here you go (from [http://www.linux.com/articles/114181](http://www.linux.com/articles/114181) ):

> The installation process creates a new print queue for the Officejet 5610, this one exclusively for fax use. But it's still not quite ready to use at this point. In order to send a document you've prepared in OpenOffice.org, for example, you need to run hp-sendfax from the command line.

From the hp-sendfax screen, enter the phone number, select a cover page, and otherwise prepare to fax you document. Then, from within OpenOffice.org, print the document to the fax printer queue, and you're done. The Officejet 5610 takes over from there, dialing the assigned number and putting your fax on the line. 

---

