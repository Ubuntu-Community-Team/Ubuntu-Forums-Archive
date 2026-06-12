---
title: "converting doc to pdf"
date: 2008-01-22
forum: General Help
---

### Post by jsvidyad on 2008-01-22
Hi!!

   Is there a command line utility that can convert .doc files and .odt files to pdf?? 

      Thank you in advance for your help.

---

### Post by mathnerd314 on 2008-01-22
I generally use the "Print to PDF" thingamajig in OpenOffice. I'm not sure if there's a command line utility, though... why do you specifically need one?

---

### Post by jsvidyad on 2008-01-22
I need to write a script that automates the conversion fo files to pdf. So, for that I need to access the program from the command line.

---

### Post by cdenley on 2008-01-22
```
sudo apt-get install wv tetex-extra ghostscript
wvPDF test.doc test.pdf
```

---

### Post by jsvidyad on 2008-01-23
Hi!!


   i tried using wvPDF, but it is giving conversion errors for a doc file created using Word 2003 containing tables. But OpenOffice can export files to PDF. Is there any way to access this functionality from the command line without having to open an OpenOffice window??

---

### Post by cdenley on 2008-01-23
You might be able to if you set up a pdf generator as a printer in cups. Check out "man oowriter".

---

### Post by stchman on 2008-01-23
> **jsvidyad said:**
> Hi!!

   Is there a command line utility that can convert .doc files and .odt files to pdf?? 

      Thank you in advance for your help.

I don't know of a CLI tool, but you can use the package cups-pdf or the print to PDF tool in Openoffice.

---

### Post by Focx on 2008-02-21
I'm trying the same right now using wvPDF, but as this does not work for you, maybe you'd like to have a look here:
[http://www.oooforum.org/forum/viewtopic.phtml?t=3772&postdays=0&postorder=asc&start=0]("http://www.oooforum.org/forum/viewtopic.phtml?t=3772&postdays=0&postorder=asc&start=0")

---

### Post by Coort on 2008-02-21
```
sudo apt-get install cups-pdf
```

As someone suggested above, this will install on your system a virtual PDF printer (like PDFGenerator do on Windows, if you know the tool), all program that can print should see this printer as a normal one and generate a PDF output file (i think default is ~ or ~/PDF, i don't remember now 'cause i've changed it some time ago).

---

### Post by reda_ea on 2008-03-13
cups-pdf was already installed on my stsem ... anyway what i did newt was

1. System > Administration > Printing and created a new printer, chose it as a PDF file printer, and named it "pdf"

2. that's all, now just run 
```
oowriter -pt pdf the_word_file.doc
```
you'll find your pdf file in ~/PDF

---

### Post by 1oki on 2008-03-17
A very simple way to do this from command line is to install "abiword" (apt-get install abiword)

use this syntax after you installed:


> for i in DOCNAME.doc ; do abiword --to=pdf $i ; done

Change DOCNAME.doc to whatever the document's name is... if you want to do more than one doc, just replace the name with a "*" and your good to go!

---

