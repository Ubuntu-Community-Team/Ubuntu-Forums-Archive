---
title: "Fonts not printing right"
date: 2006-11-15
forum: General Help
---

### Post by Carandol on 2006-11-15
I've designed a CD cover in OpenOffice Draw (in Dapper) using the "Purisa" font. It looks fine on screen, but when I print it out on my Epson Photo Stylus R200, the wider letters such as W and M are cut off on the right hand side. I don't know if this is a hardware or a software problem, or where to start trying to fix it. Any help appreciated!

---

### Post by geraldf on 2006-11-30
Hi Carandol,

when using OOo 2.0.4 unter Ubuntu 6.10 I have the same problem with different printers:
HP PSC 1610 (ink)
HP LaserJet 4L (laser, rather old)
Both are non-Postscript printers and use the hpijs filter.

Some letters (e. g. W, m, @) are cut off on the right side.
German Umlauts (ÄÖÜ) are cut off on top and lose their dots.

The problem occurs with several fonts, e. g. Bitstream Vera Sans, but not with Arial.

---

### Post by geraldf on 2006-12-06
Does anyone else have this problem?

---

### Post by NicoNess on 2006-12-06
Yes I ( We) have the same problem with ubuntu edgy and dapper drake with font " bitstream vera ". 
2 days ago I have posted the following forum.
[http://ubuntuforums.org/showthread.php?t=312592]("http://ubuntuforums.org/showthread.php?t=312592")

And also a forum in the [french ubuntu]("http://forum.ubuntu-fr.org/viewtopic.php?id=80770") web site.

We have not found any solution yet.
When I run ubuntu edgy eft with on the liveCD , the printing output for "bitstream vera" is correct. No "M" truncated.

If it is possible the fonts can be corrupted ?

Do somebody knows how to compare my actual list of package version with the official edgy eft version ? I was wondering that a package update "corrupts" the font rendering.

Thanks

Nico

---

### Post by geraldf on 2006-12-06
Thank you Nico!

Your posting [http://ubuntuforums.org/showthread.php?t=312592]("http://ubuntuforums.org/showthread.php?t=312592") covers the same problem.

---

### Post by budgie9 on 2006-12-06
I can't help you guys a lot here, but I did try printing from OOo myself a few minutes ago. in English and the fonts worked fine. I use a Canon Inkjet i860.

I have as it happened just downloaded all the free TrueType fonts and many others.
Can I suggest you try dowloading or reloading the fonts. They may well be corrupt but I suspect it is more likely your hardware.
A trick we used to play in the days of the Sinclair Ql was to print ALL the fonts out in a reasonable size to see what was wrong if anything. To make sure things are not being truncated by the printer print in Landscape.

---

### Post by NicoNess on 2006-12-07
> Can I suggest you try downloading or reloading the fonts.

How can I download ( which package ?) fonts again, or how to reload the fonts ? Via synaptic or apt-get ?
I try a command like dpkg-reconfigure fontconfig, but nothing has changed.

I try to print out in several printers, and in files like postscript generic printer, and the result is always with truncated letters.

---

### Post by malmjako on 2006-12-14
I just noticed this problem too. It seems most of my TrueType fonts (e.g. Arial, Bitstream Vera, Free Serif, Gentium, jGaramond, Trebuchet MS, Verdana) have some problems with printing - especially W, Å, Ä, and Ö. Type1 fonts do NOT have this problem (e.g. Nimbus *, URW *).

This problem arises when I print from OpenOffice, AbiWord, Evince, Acroread. It does NOT arise when printing from Scribus. All print directly from Scribus seems ok. This is true both for printing to printer and to a postscript file.

My printer is a HP Photosmart 3210, using the HPLIP driver, running on Edgy.

Postscript file from OpenOffice: [http://jakob.malms.org/tmp/typsnittstester.ps](http://jakob.malms.org/tmp/typsnittstester.ps)
OpenOffice source document: [http://jakob.malms.org/tmp/typsnittstester.odt](http://jakob.malms.org/tmp/typsnittstester.odt)
Postscript file from Scribus: [http://jakob.malms.org/tmp/typsnittstester_scribus.ps](http://jakob.malms.org/tmp/typsnittstester_scribus.ps)
Scribus source document (1.3.3.4, scribus-ng Edgy package, same results with 1.2.4.1, scribus package): [http://jakob.malms.org/tmp/typsnittstester_scribus.sla](http://jakob.malms.org/tmp/typsnittstester_scribus.sla)

---

### Post by theProf on 2006-12-14
Same issue here with Purisa font on HP Desket 952C with hp driver on Edgy.  I'm trying to print Christmas Card envelopes and I have to use a Bitstream font instead.

---

### Post by malmjako on 2006-12-15
May I suggest you use scribus (see my post above)? I think you will find it to be an excellent Cristmas Card application! ;-)

For the latest version (much nicer than the version in the "scribus" package, especially with detecting your fonts...):
```
sudo apt-get install scribus-ng
```

Has anyone seen other (English) posts about this issue in other Linux forums? I tried to look through the French posts. It seems nobody else has tried Scribus. It seems the problem lies in the way the postscript is generated... Are all prints first converted to postscript?

---

### Post by malmjako on 2006-12-16
I decided to install AFPL GhostScript 8.54 and use that instead of gs-esp which is included with Edgy. All characters seem to print correctly from other programs as well now. One other problem arose, however: I can't print directly from OpenOffice! Trying to print to a ps-file doesn't work either. Any ideas to why this happened? If I export to PDF and print from, say, Evince everything works ok.

---

### Post by malmjako on 2006-12-22
AFPL Ghostscript 8.54 installed from source seems to have given me some trouble with showing EPS figures saved from Octave/Gnuplot. (Something about fonts...) So I installed gs-gpl from the repositories, which is at version 8.50. It seems (without very extensive testing) that the problems with cut-off characters as well as printing from OpenOffice and opening the above mentioned EPS figures have all been taken care of.

---

