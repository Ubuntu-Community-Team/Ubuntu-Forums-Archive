---
title: "printing to pdf"
date: 2007-11-30
forum: General Help
---

### Post by rkakkar on 2007-11-30
Hi guys,

Currently I'm using the default printer driver that comes with ubuntu and select 'print to file' and name the extension .pdf whenever I want to take a pdf printout. The file opens successfully in evince but I'm unable to open it in Adobe Reader on windows. I'm suspecting the default driver with the 'print to file' option isn't exactly for pdf files. So how can I set up a default printer to print pdf files (which can be read by Adobe) from basically any linux program?

Thanks!

---

### Post by kushal.kumaran on 2007-11-30
Using "Print to File" will create a PostScript file (use the extension .ps for these).  You can convert these to pdf files using the ps2pdf program.  This is part of the ghostscript package.

Alternatively, the cups-pdf package has a pdf output driver to generate pdf files directly.  By default, it will place the generated pdf files in the ~/PDF directory.

HTH

---

### Post by rkakkar on 2007-11-30
hey thanks kushal... will give it a whirl....

---

