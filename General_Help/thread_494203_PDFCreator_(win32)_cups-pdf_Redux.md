---
title: "PDFCreator (win32) cups-pdf Redux"
date: 2007-07-06
forum: General Help
---

### Post by flaxeater on 2007-07-06
So I have recently really switched from windows to Ubuntu for real, instead of this half in half out thing I have been doing. 

[http://sourceforge.net/projects/pdfcreator/](http://sourceforge.net/projects/pdfcreator/)

I've used PDFCreator for windows for years and it's good.  It makes reasonable sized PDF's, however cups-pdf does not make reasonable size pdf's.   Cups makes a 20 meg pdf and prints a 33 meg file.  I had been successfully saving a lot of space by printing big pdf's through PDFCreator.  

PDF Creator is built on top of GhostScript which is AFAIK what runs linux PostScript stuff.  I'm baffled as to why there is such a difference.  

Things I have tried.  

pdfopt (A ghostcript tool)
pdftk (pdf tool kit specifically pdftk .. output .. uncompress ; pdf .. output .. compress)
I tried installing acrobat but there was no magic there either.

Does anyone have a suggestion on how to produce under 10mb pdfs from a 16 page document in Linux?

---

### Post by dwiedenfeld on 2007-09-12
I have the same question. Anyone?

---

### Post by aum11 on 2007-09-16
Is the following of any help?

[http://www.howtoforge.com/editing_pdf_files_pdfedit_ubuntu_feisty](http://www.howtoforge.com/editing_pdf_files_pdfedit_ubuntu_feisty)

---

### Post by CrazyIndians on 2008-04-20
I am also looking for the same can anyone help us out

---

### Post by Linux&amp;Gsus on 2008-04-20
May I ask what "16 page document" exactly means? How do you print your PDF?
Just out of curiosity I made a 24 page document (looked for a howto website with loooong text) and then made a PDF out of that. This is plain text, no images, but 24 pages. 184kb. No trick, no magic, I just pasted the text into OpenOffice and hit the PDF button.

BTW, many applications have the ability to export to PDF and often you can adjust some things, e.g. image compression, etc. Make sure that you export a PDF for screen, not print. That makes a huge difference.

Cheers,
Steve

---

### Post by xrat on 2008-06-27
I, too, was looking for a way to decrease the size of PDFs. In my concrete case, I had a PDF of 8 pages scanned in with XSane, ie. 8 pictures, full color, 100 dpi, no compression, this leads up to 10 MB.

I did manage to compress this PDF but I was not happy with how I did it, nor with what I found is available for the task (though this might be just me too stupid to find a better solution).

On the way, I tried pdfedit. AFAIK, it does not allow to compress images.

Eventually, I did it with [gscan2pdf]("http://gscan2pdf.sourceforge.net/") (there is a package for Ubuntu). I loaded the PDF with GIMP. Then, I saved the pages to uncompressed TIF and imported them into gscan2pdf.

Gscan2pdf comes with its own PDF export. That's good. It also allows to set meta-data. One thing that I found missing was a way to set the page size.

(I first saved the pages to PNG. But the resulting PDF was about 20 inches(!) wide -- maybe a bug in gscan2pdf. It did work with TIF.)

HTH.

---

### Post by kaibob on 2008-06-27
Deleted by kaibob

---

### Post by prankst3r on 2008-06-30
> **xrat said:**
> I, too, was looking for a way to decrease the size of PDFs. In my concrete case, I had a PDF of 8 pages scanned in with XSane, ie. 8 pictures, full color, 100 dpi, no compression, this leads up to 10 MB.

I did manage to compress this PDF but I was not happy with how I did it, nor with what I found is available for the task (though this might be just me too stupid to find a better solution).

On the way, I tried pdfedit. AFAIK, it does not allow to compress images.

Eventually, I did it with [gscan2pdf]("http://gscan2pdf.sourceforge.net/") (there is a package for Ubuntu). I loaded the PDF with GIMP. Then, I saved the pages to uncompressed TIF and imported them into gscan2pdf.

Gscan2pdf comes with its own PDF export. That's good. It also allows to set meta-data. One thing that I found missing was a way to set the page size.

(I first saved the pages to PNG. But the resulting PDF was about 20 inches(!) wide -- maybe a bug in gscan2pdf. It did work with TIF.)

HTH.

I'm not sure what version of gscan2pdf you are using, but the newest versions allow you to import PDF's, so the conversion to TIFFs step would be unecessary. A note - not all PDFs will import properly into gscan2pdf - i think this is more often the case where the pdf contains more than just images.

---

### Post by xrat on 2008-07-22
Thanks prankst3r, I did not know that newer versions of gscan2pdf can import PDF directly. I was using gscan2pdf v0.9.21 which comes with Ubuntu 8.04. As you said, gscan2pdf cannot import all PDFs though. When I just tried 5 randomly picked PDFs it unfortunately failed on all of them. Nevertheless, one should try this first. If it does not work there are still the workarounds.
Cheerio.

---

