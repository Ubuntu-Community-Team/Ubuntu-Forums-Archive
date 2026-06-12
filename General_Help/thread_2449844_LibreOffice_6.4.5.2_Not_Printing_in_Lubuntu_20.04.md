---
title: "LibreOffice 6.4.5.2 Not Printing in Lubuntu 20.04"
date: 2020-09-03
forum: General Help
---

### Post by rbscairns on 2020-09-03
I recently replaced Windows 10 with Lubuntu 20.04 on my PC and ran Apply Full Upgrade. Lubuntu includes LibreOffice 6.4.5.2. My printer is a Brother HL-2140 and is working properly with all applications **except** LibreOffice. When I try to print in LO with default settings, all my printer does is produce a blank page. I also tried to print to file and all that was produced was a blank pdf.

The same printer works perfectly with LO 6.0.7.3 on another 32 bit PC under Lubuntu 18.04.

How can I get LO 6.4.5.2 to print properly in Lubuntu 20.04?

---

### Post by guiverc on 2020-09-03
Try the following

(tested on my Lubuntu *groovy* using a brother HL-2142; it was tested long ago too using Lubuntu 20.04)

```
env SAL_VCL_QT5_USE_CAIRO=true libreoffice --writer
```

which is a command to start LibreOffice Writer (*adjust for other libreoffice tool or you can leave the '--writer' off too*).  Load whatever document you are trying to print, and print it. Is that any better?

It's covered in [https://discourse.lubuntu.me/t/printing-problem-with-20-04/964](https://discourse.lubuntu.me/t/printing-problem-with-20-04/964) (a rather long post) where they mention making a Desktop icons too.

 For help on creating desktop icons (ie. a LibreOffice icon using this command so you can print) you can refer to the Lubuntu manual page found at [https://manual.lubuntu.me/stable/5/5.2/desktop_icons.html](https://manual.lubuntu.me/stable/5/5.2/desktop_icons.html)

---

### Post by gdenton61 on 2020-09-03
I had this same issue yesterday, I found I had to set printer language to Postscript:

File
Printer Settings...
Properties...
Device tab
Printer language type = Postscript Level 1
OK

But I did just notice that it doesn't keep this setting, I'll try to figure out how to make it permanent.

---

### Post by rbscairns on 2020-09-03
Thank you gdenton61. It worked but only for one print job. After that File>Print Settings>Properties>Device>Printer language type: would not accept any of the PostScripot Level setting and my problem persists. I even tried after rebooting everything and this persisted.

I also still have the blank page problem with printing to file (pdf).

---

### Post by rbscairns on 2020-09-03
> **guiverc said:**
> Try the following

(tested on my Lubuntu *groovy* using a brother HL-2142; it was tested long ago too using Lubuntu 20.04)

```
env SAL_VCL_QT5_USE_CAIRO=true libreoffice --writer
```

which is a command to start LibreOffice Writer (*adjust for other libreoffice tool or you can leave the '--writer' off too*).  Load whatever document you are trying to print, and print it. Is that any better?

It's covered in [https://discourse.lubuntu.me/t/printing-problem-with-20-04/964](https://discourse.lubuntu.me/t/printing-problem-with-20-04/964) (a rather long post) where they mention making a Desktop icons too.

 For help on creating desktop icons (ie. a LibreOffice icon using this command so you can print) you can refer to the Lubuntu manual page found at [https://manual.lubuntu.me/stable/5/5.2/desktop_icons.html](https://manual.lubuntu.me/stable/5/5.2/desktop_icons.html)

I tried this and LibreOffice opened with a new write document. I could not open an existing document that I wanted to print. Before LibreOffdice opened, terminal returned:
```
$ env SAL_VCL_QT5_USE_CAIRO=true libreoffice --writer
javaldx: Could not find a Java Runtime Environment!
Please ensure that a JVM and the package libreoffice-java-common
is installed.
If it is already installed then try removing ~/.config/libreoffice/4/user/config/javasettings_Linux_*.xml
Warning: failed to read path from javaldx
Icon theme "elementary" not found.
```
I checked and both Java Runtime Environment and libreoffice-java-common are installed. I then deleted ~/.config/libreoffice/4/user/config/javasettings_Linux_*.xml however the problem of not being able to open another odt file persisted.

---

### Post by gdenton61 on 2020-09-04
OK I found this on another site and seems to work for me:

Close every document opened by LibreOffice. 
Go to LibreOffice main application (not writer or calc, etc..)
Tools
Options
LibreOffice node in treeview
Print
Un-check the "PDF as Standard Print Job Format" box
OK


Then in Calc or Writer...
File
Printer Settings...
Properties...
Device tab
Printer language type = Postscript Level 1
OK

---

### Post by rbscairns on 2020-09-06
> **gdenton61 said:**
> OK I found this on another site and seems to work for me:

Close every document opened by LibreOffice. 
Go to LibreOffice main application (not writer or calc, etc..)
Tools
Options
LibreOffice node in treeview
Print
Un-check the "PDF as Standard Print Job Format" box
OK


Then in Calc or Writer...
File
Printer Settings...
Properties...
Device tab
Printer language type = Postscript Level 1
OK

Thank you. That works perfectly!

---

### Post by ronbot77 on 2020-09-09
Great, that helped me for printing. There also is a problem with generating pdf: The pages created are blank. The Check-box for "use pdf as standard" is greyed out. Any Ideas? Thank you!

---

### Post by ronbot77 on 2020-09-09
I found the solution at

[https://ask.libreoffice.org/en/question/242188/cannot-print-anything-exporting-to-pdf-produces-blank-pdf-lubuntu-2004/](https://ask.libreoffice.org/en/question/242188/cannot-print-anything-exporting-to-pdf-produces-blank-pdf-lubuntu-2004/)

You have to remove libreoffice-qt5. Now my PDF looks fine :-)

---

