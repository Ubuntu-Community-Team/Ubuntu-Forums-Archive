---
title: "Export to PDF"
date: 2006-07-16
forum: General Help
---

### Post by wizzkid on 2006-07-16
Hi. Is there any software for kubuntu that export PDF from any program like jpg, gif, bmp. doc etc.? I know there an export functionality in Openoffice, but I want something that exports jpg and other file format. I want something like FinePrint pdfFactory in windows.

thanks a lot.

---

### Post by yopnono on 2006-07-16
> **wizzkid said:**
> Hi. Is there any software for kubuntu that export PDF from any program like jpg, gif, bmp. doc etc.? I know there an export functionality in Openoffice, but I want something that exports jpg and other file format. I want something like FinePrint pdfFactory in windows.

thanks a lot.

Install CUPS-PDF
[http://ubuntuforums.org/showthread.php?t=188860](http://ubuntuforums.org/showthread.php?t=188860)

---

### Post by wizzkid on 2006-07-17
Thanks a lot :)

---

### Post by wizzkid on 2006-07-17
I followed the link. [http://ubuntuforums.org/showthread.php?t=188860](http://ubuntuforums.org/showthread.php?t=188860)
> 
   1. Install the cups-pdf package (I used version 2.2.0-1)
   2. Go to System -> Administration -> Printing
   3. Doubleclick "New Pinter"
   4. Notice that there is no mention of a CUPS PDF printer
   5. Open a terminal and tpe "sudo nautilus" and then your password
   6. Go to Filesystem -> usr -> lib -> cups -> backend
   7. Rightclick "cups-pdf" and select Properties
   8. Go to the Permissions tab and click the "Set user ID" special flag
   9. Again try to add a new printer
  10. There is now a "PDF Printer" detected, select it
  11. Select the Generic, Postscript Color Printer (Rev 3b)
  12. Give it a name, like PDF Printer
  13. Right click on the newly created printer, and select Properties
  14. Click "Print a Test Page"
  15. The file should be in your Home folder, under the PDF folder



- When I right click the cups-pdf, properties then permission, I coudnt find the Set user ID.. 
- When I add new printer, I could find PDF Printer.
- I couldt find Postscript Color Printer (Rev 3b)
- On my Kubuntu 6.06. there's a print to file (pdf) on the list of installed printers, but it didnt show up on gimp and other programs except for kate. 

any suggestions? :)

---

### Post by wizzkid on 2006-07-17
No need to response... I solved the problem :) 

Thanks a lot for the suggestion :)

---

### Post by clarkth on 2006-07-17
what was the solution?

---

### Post by wizzkid on 2006-07-18
Add printer > other printer type > Virtual Printer >
Then click on the PostScript Printer, then Generic printer will be selected, just press next and follow the instruction... :)

It should work :)

---

