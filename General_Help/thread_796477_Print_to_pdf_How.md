---
title: "Print to pdf? How?"
date: 2008-05-16
forum: General Help
---

### Post by knottshawk on 2008-05-16
Okay, on windows I use a program called cutePDF that allows me to print to PDF. Now before you guys all jump me and tell me that I can print to pdf by default in xubuntu, I've discovered that the built in pdf printer in xubuntu doesn't produce searchable pdf files.

cutePDF captures text and the text is still searchable. The pdf printer in xubuntu is essentially creating an image.

Tips? Ideas?

---

### Post by mannheim on 2008-05-16
I'm using ubuntu (with gnome) not xubuntu, but printing to pdf works fine here and produces a searchable pdf (e.g. from firefox, from a text editor or whatever).

In ubuntu, the package responsible for this is cups-pdf. I guess that both ubuntu and xubuntu use cups, and that they can both therefore use cups-pdf. Do you have cups-pdf installed?

---

### Post by knottshawk on 2008-05-16
Yeah... cups is the default one. So do you tell it to print to file? I have to tell it to print to file, then add the extension .pdf.
If I don't do that it saves it as a postscript file.

---

### Post by mannheim on 2008-05-16
In ubuntu, it's not just "cups", but the "cups-pdf" package that needs to be installed. That package creates another "printer" which shows up alongside all the other configured printers, with the name "PDF". You then have to select the "PDF" printer when printing.

Is cups-pdf installed? If not, try "sudo apt-get install cups-pdf" to install it.

There's an (out-of-date?) howto with some suggestions for xubuntu posted [here]("http://ubuntuforums.org/showthread.php?t=188860&page=6").

---

### Post by knottshawk on 2008-05-19
According to Nautilus I already have cups-pdf. When I go to print in firefox, the only printer I have as an option is "PostScript/default". So where is this pdf printer I'm supposed to have?

I can FORCE the postscript printer to print a pdf by telling it to print to file and naming it filename.pdf, but that's less than ideal. Especially since that doesn't seem to produce a searchable pdf.

Ideas?

---

### Post by fsmithred on 2008-05-19
I can find the pdf printer in Epiphany, Konqueror, and gedit, but not in firefox. When you "force" it by naming your file as something.pdf, I'm pretty sure you're just making a postscript file with a name that ends in .pdf.

---

### Post by CREEPING DEATH on 2008-05-19
You have to go to "Printers" and set up cups-pdf.  I have a physical printer, but cups-pdf is my default to prevent any waste of ink and paper.

CD

---

### Post by utUtu on 2008-05-19
> **knottshawk said:**
> According to Nautilus I already have cups-pdf. When I go to print in firefox, the only printer I have as an option is "PostScript/default". So where is this pdf printer I'm supposed to have?

I can FORCE the postscript printer to print a pdf by telling it to print to file and naming it filename.pdf, but that's less than ideal. Especially since that doesn't seem to produce a searchable pdf.

Ideas?

Look in synaptics if cups-pdf is installed.

---

