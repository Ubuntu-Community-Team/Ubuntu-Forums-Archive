---
title: "How to install Acrobat Reader into Xubuntu 14.04"
date: 2015-10-29
forum: General Help
---

### Post by Ralph L on 2015-10-29
I am running xubuntu 14.04.  As is well known Adobe stopped support of Acrobat Reader for Linux.  However, I have a "fill in the blanks" pdf form that I need to use.  Neither Evince nor qpdfview will perform this function.  In fact neither will even display the form so that I can copy it into LibreOffice Writer.  I found this site ([http://ubuntuhandbook.org/index.php/2014/10/install-adobe-reader-ubuntu-14-10/](http://ubuntuhandbook.org/index.php/2014/10/install-adobe-reader-ubuntu-14-10/) ) that says how to install Reader.  I followed the instructions and indeed it was installed, and at least it displayed the .pdf form.  However, I still couldn't fill it out correctly.  Does anyone know if there is a later version that works under linux???

Also, if this is the best version of Reader that is available, how can i copy the repository to my computer, so that I can install it into future systems, in case the present repository goes away.?

---

### Post by Sweet_Baby_Jamie on 2015-10-29
You need a pdf annotator.  Ubuntu has one called [**Xournal**]("http://xournal.sourceforge.net/") which is easy to use, and there are a couple of others in the repositories I bet.

---

### Post by Ralph L on 2015-10-30
Thanks for the response.  I appreciate it.  I installed xournal, but it wouldn't open my .pdf file.  I got the following message instead:```
Please wait... If this message is not eventually replaced by the proper contents of the document, your PDF viewer may not be able to display this type of document. You can upgrade to the latest version of Adobe Reader for Windows®, Mac, or Linux® by visiting http://www.adobe.com/products/acrobat/readstep2.html. For more assistance with Adobe Reader visit http://www.adobe.com/support/products/ acrreader.html.
```  This is the same message I get from Evince and qpdfview.  Only Adobe Reader opens the file.  I would appreciate any other ideas you might have.

---

### Post by mastablasta on 2015-10-30
what about Okular?

also Libre office Draw can import PDFs.

---

### Post by slickymaster on 2015-10-30
> **Sweet_Baby_Jamie said:**
> You need a pdf annotator.  Ubuntu has one called [**Xournal**]("http://xournal.sourceforge.net/") which is easy to use, and there are a couple of others in the repositories I bet.
I don't think Xournal is capable of doing what the OP intends. Xournal is an application for note taking, sketching, keeping a journal using a stylus and the OP is probably referring to the capacity of working with pdf's forms.
> **mastablasta said:**
> what about Okular?
also Libre office Draw can import PDFs.
+1 to Okular

---

### Post by Sweet_Baby_Jamie on 2015-10-30
I open Xournal, choose "Annotate PDF," then locate and select the PDF I want to annotate.  Alternately I can open my file manager, navigate to the PDF file I want to fill out or annotate, *right*-click on it and select "Open With..." and then choose Xournal.

Xournal is a cool note-taking and sketch app, but it *does* annotate PDFs.

---

### Post by HermanAB on 2015-10-30
If the PDF has XFA forms, then you need Master PDF Editor.  It is the only one I know of that can do it.

---

### Post by coldraven on 2015-10-30
I found this slightly elderly link, if the pdf does not have too many pages it might be worth a try. I personally would do it to send back a pdf that is actually "portable"!
[http://www.troubleshooters.com/linux/pdf2gimp2pdf.htm](http://www.troubleshooters.com/linux/pdf2gimp2pdf.htm)

---

