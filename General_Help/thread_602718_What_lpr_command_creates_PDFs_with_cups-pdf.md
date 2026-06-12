---
title: "What lpr command creates PDFs with cups-pdf?"
date: 2007-11-04
forum: General Help
---

### Post by emendelson on 2007-11-04
I've installed cups-pdf, and can easily create PDF files from any Linux application that I try (the output files go into ~/PDF). The name of my cups-pdf printer is PDFprinter.

I'm now trying to create PDFs from a DOS application in DOSEMU, and the technique that I'm trying to use is to "print" the PostScript output from the DOS application to cups-pdf. I can easily print from DOSEMU to a physical PostScript printer (my default printer) by setting this entry in dosemu.conf (this is also the default setting):

$_lpt1 = "lpr -l"

The instructions in dosemu.conf say this:

# Print commands to use for LPT1, LPT2 and LPT3.
# Default: "lpr -l", "lpr -l -P lpt2", and "" (disabled)
# Which means: use the default print queue for LPT1, "lpt2" queue for LPT2.
# "-l" means raw printing mode (no preprocessing).

I've tried various ways of setting up this option, such as:

$_lpt1 = "lpr -l -P PDFprinter"

but nothing works, and CUPS reports that printing to the PDFprinter has failed.

Does anyone know the correct command to use here?

Many thanks!

---

### Post by fragos on 2007-11-04
The print to PDF function looks like a device and can be selected as default.  It has it's own device URI which you can use.

---

### Post by emendelson on 2007-11-04
Thank you for that reply. As you say, the device URI is 

cups-pdf:/

But I'm still absolutely puzzled as to what to put in the string in dosemu.conf:

$_lpt3 = ""

Could you suggest exactly what might go there that would allow printing to PDF?

Thanks again.

---

### Post by emendelson on 2007-11-04
To answer my own question: the problem was the -l that I put in the printer command.

$_lpt3 = "lpr -P PDFprinter"

(where PDFprinter is the name of my cups-pdf printer) works correctly; the output is named _stdin_.pdf. 

Now to try to figure out a way to add a number to all new PDFs so that I can print multiple files...

---

