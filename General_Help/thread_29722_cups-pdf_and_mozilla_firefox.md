---
title: "cups-pdf and mozilla firefox"
date: 2005-04-25
forum: General Help
---

### Post by guardian653 on 2005-04-25
I'm having some issues with cups-pdf. I installed it mainly for printing pdf from within Firefox, but for some reason when I view the pdf in xpdf and gpdf no text is shown! However if I use ghostscript the text does display, but all garabled. I also tried doing a straight conversion from ps to pdf using ps2pdf--same prob. Graphics, borders, etc show up fine, just not the text! Anyone have ideas for this?

Thanks

edit: here is the output of xpdf

```
david@davehome:~/cups-pdf$ xpdf -freetype yes _Times_New_Roman_Regular_0_0_mozilla_printout_Xv594RDD6oUELhWJXyI27MjT2yM__0____0_.pdf
Warning: Cannot convert string "-*-times-medium-r-normal--16-*-*-*-*-*-iso8859-1" to type FontStruct
Error: Unknown character collection 'mozilla_printout-1S8OOC+RiYcSF8HmkiSG6AnrNT0='
Error: Unknown character collection 'mozilla_printout-Xv594RDD6oUELhWJXyI27MjT2yM='
Error: Unknown character collection 'mozilla_printout-AN9oU9SozqGSdDaMwYb+McuTvv4='
Error: Unknown font tag 'R16'
Error (276): No font in show
Error: Unknown font tag 'R16'
Error (293): No font in show
Error: Unknown font tag 'R16'
Error (320): No font in show
Error: Unknown font tag 'R24'
Error (550): No font in show
Error: Unknown font tag 'R24'
Error (602): No font in show
Error: Unknown font tag 'R31'
Error (620): No font in move/show
Error: Unknown font tag 'R24'
Error (650): No font in move/show
Error (685): No font in show
Error: Unknown font tag 'R31'
Error (700): No font in show
Error (712): No font in show
Error (720): No font in show
Error (805): No font in move/show
Error (807): No font in show
Error (836): No font in move/show
Error (844): No font in move/show
Error (855): No font in move/show

```

---

### Post by ape on 2005-04-26
I was having the same problem till I added this in front of the lpr command listed in the properties of the printer that you have set up to print to the cups-pdf device:

gs -q -sDEVICE=pswrite -sOutputFile=- -dNOPAUSE -dBATCH -d
MozConvertedToLevel2=true - | lpr (rest of the existing lpr command)

The resultant pdf file is viewable through xpdf now.  Good luck.

---

### Post by guardian653 on 2005-04-28
Sorry for the late reply, it does show up in xpdf now! Thanks!

EDIT:
After testing some more I notice that xpdf is rendering the text very slowly, am I missing something? Other PDFs off the net (Most of them made with Adobe's Distillier) render quick with AA text and nice graphics. However the PDFs I make the text is somewhat overdone and in some cases the letter spacing is cramp.

My print string:
gs -q -sDEVICE=pswrite -sOutputFile=- -dNOPAUSE -dBATCH -dMozConvertedToLevel2=true - | lpr ${MOZ_PRINTER_NAME:+'-P'}${MOZ_PRINTER_NAME}

---

### Post by ape on 2005-04-29
I'd kind of noticed this also, but only when viewing the .pdf.  Printing it out showed the text as I would expect it to appear.

I think the issue is with the level of postscript that xpdf can handle as I noticed that without the gs command in the print line, ggv can view the files just fine.

Where I first though of trying this command was due to a printer page that Firefox printed out for me at work that said the printer I was trying to print to didn't have a new enough version of the postscript firmware installed and I would need to use this command to convert the postscript output to level 2 to send to the printer.

---

### Post by paretooptimum on 2005-05-09
Other pages worked fine (e.g. text from AbiWord, but FIrefox pages were text-less - they had the images and such but no text.

Here is what worked for me to fix with a very recent install...

REVISED:

Tried to view file in Acrobat on a windws machine and it all looked fine.

THEREFORE: Install Acrobat Reader 7 and it all works fine

Available from Marillat repository (see ubuntu guide [http://ubuntuguide.org/](http://ubuntuguide.org/))

Sorry xpdf and evince, keep trying

Hope this helps

---

### Post by paretooptimum on 2005-05-09
AH HA! The plot thickens!!!

From [https://bugzilla.ubuntu.com/show_bug.cgi?id=10087](https://bugzilla.ubuntu.com/show_bug.cgi?id=10087)

The current (2005-04-23) CVS version of freetype2 fixes some
problems where certain PDF viewers would miss characters.
See [https://bugs.freedesktop.org/show_bug.cgi?id=2719](https://bugs.freedesktop.org/show_bug.cgi?id=2719) for
more details. It would be nice to have these fixes included
in Ubuntu freetype2 packages.

Notice the "It would be nice... Ubuntu" line.

---

### Post by Pond on 2005-09-28
There seems to be a simpler solution, at least under the Breezy Badger preview release (5.10). Use the menu entry "[FONT="Courier New"]System->Administration->Printing[/FONT]" to get the Printers window up, then open the Properties dialogue box for the PDF printer. In the "Advanced" tab, choose a "GhostScript pre-filtering" value that is anything other than "No pre-filtering". "Convert to PS level 2" is a reasonable choice. The PDFs written by cups-pdf will then have text legible under applications including both gpdf and xpdf.

Note that certain spacing irregularities, bounding box problems and header/footer positioning errors may be apparent, but then, Firefox seems to do an equally bad job under Windows, so I think the problem lies with that rather than any PostScript translation going on within the CUPS.

Just in case it makes any difference - I'm using an HP LaserJet 9065-MFP printer definition with the recommended Postscript driver, at 300 DPI to A4 paper. It is "connected" to the auto-detected PDF Printer rather than on the "Virtual Printer (PDF Printer)" port.

**Edit** - Ah, except that does produce pretty ropey PDFs - text as images, not text. Still, it gives pretty wide compatibility with lots of PDF viewers. The tip about using Acroread is seconded; Adobe Reader 7.x seems to be able to handle the Firefox printouts OK. Given the filename oddities and other tricks, I presume Firefox is using a higher level of PS than most with, in all probability, some variant of wide character set support that's not understood by lots of viewers.

---

### Post by krismatth3 on 2006-04-12
This is a bit after the fact, but I had the same problem today. It happened because I chose the color postscript driver. Changing the driver afterwards did not fix it. The way I fixed it was to completely remove that printer entry and add a new one using the regular postscript driver.

evine and xpdf both view the output files nicely now.

---

