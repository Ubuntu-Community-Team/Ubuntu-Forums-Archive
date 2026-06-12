---
title: "Is there a way to alter a PDF file with Linux utilities?"
date: 2007-09-05
forum: General Help
---

### Post by tc101 on 2007-09-05
Is there a way to alter a PDF file with Linux utilities?  On my system, PDFs are opened with 
Evince 0.8.1 Document Viewer.   I don't think it allows me to alter a PDF. 

Someone sent me an application as a PDF file.  I would like to just fill it out on my computer and email it back to them, rather than print it out, fill it out by hand and fax it to them.  Is there a way to do this?

---

### Post by testube_babies on 2007-09-05
You might want to try PDFEditor or Scribus:
[http://www.getdeb.net/app.php?name=PDF+Editor](http://www.getdeb.net/app.php?name=PDF+Editor)
[http://www.getdeb.net/app.php?name=Scribus](http://www.getdeb.net/app.php?name=Scribus)

---

### Post by wrathkeg on 2007-09-05
flpsed:

[http://www.ecademix.com/JohannesHofmann/flpsed.html]("http://www.ecademix.com/JohannesHofmann/flpsed.html")

---

### Post by tc101 on 2007-09-05
I installed flpsed using synaptic package manager, but I don't see it anywhere under Applications.

---

### Post by aysiu on 2007-09-05
If it's meant to be a form, [add the Medibuntu repositories](http://medibuntu.sos-sts.com/repository.php), and then install the *acroread-plugins* package.

If it's not created as a form, you might have to use PDFedit or KWord.

---

### Post by wrathkeg on 2007-09-05
> **tc101 said:**
> I installed flpsed using synaptic package manager, but I don't see it anywhere under Applications.
Type 'flpsed &' (no quotes) in a terminal.
WK

---

### Post by fragos on 2007-09-05
xournal.sourceforge.net allows PDF markups and then saves as PDF.  Perhaps not what you want but I found it useful.  Works well with a Wacom tablet.

---

### Post by daveshields on 2007-09-05
I ran into simiilar problems recently trying to access the specification documents for ODF and OOXML.

I found the PDF support in Ubuntu  limited, so much so that I wrote a blog post on this topic:

[http://daveshields.wordpress.com/2007/09/04/pdf-a-portable-persnickety-problematic-and-proprietary-document-format/]("http://daveshields.wordpress.com/2007/09/04/pdf-a-portable-persnickety-problematic-and-proprietary-document-format/")


I did have some success with pdftk, though it uses an unconventional command-line argument convention.   You can get  a quick idea what pdftk can do by visiting [http://www.pdfhacks.com/pdftk/]("http://www.pdfhacks.com/pdftk/")

---

