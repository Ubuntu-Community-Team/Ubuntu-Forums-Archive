---
title: "Can't print to file in color"
date: 2024-03-15
forum: General Help
---

### Post by klbogotz on 2024-03-15
I have a no longer supported application that doesn't allow saving in any format other than its own (ldf). I have to export the print job to a file. However, when I do this, the output is in black and white. How can I change this? Does it depend on the printer configured in the Printer Dialog? If so, how can I add a Dummy Printer to my system that prints in color?

---

### Post by TheFu on 2024-03-15
Print to a PDF file.  
```
sudo apt  install printer-driver-cups-pdf
```
 Use the **system-config-printer** program to add the PDF printer.  On mine, it is listed as "Generic CUPS-PDF".

I just did this.  It created a ~/PDF/ directory and dropped a PDF into it named "Test_Page.pdf" which had all the colors.

---

### Post by ajgreeny on 2024-03-15
I do not have the printer-driver-cups-pdf installed but whenever I use Ctrl+P to print anything, including a screen displayed pdf I get the option in the print dialogue either to print to my printer or to save as , ie print to file and can then choose PDF.
This has been my situation for just about as long as I can remember and I have never installed anything specifically to do this.

What version of Ubuntu are you using and what printer do you have?

---

