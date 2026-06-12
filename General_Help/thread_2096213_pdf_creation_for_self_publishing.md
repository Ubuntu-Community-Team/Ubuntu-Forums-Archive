---
title: "pdf creation for self publishing"
date: 2012-12-19
forum: General Help
---

### Post by Buntu Bunny on 2012-12-19
It appears that the world of self publishing is in cahoots with Adobe. Most of the print-on-demand services I've looked at require files to be created in Adobe Acrobat. [Lightning Source]("https://www1.lightningsource.com:443/default.aspx") is specific, requiring files to be PDF/X-1a:2001 or PDF/X-3:2002 compliant. (Adobe Acrobat Pro versions 6 or 7 and above respectively).

Of course there is no Adobe Acrobat for Linux. In my research I found [PDF Studio]("http://www.qoppa.com/pdfstudio/"), which comes in a Linux version, but the information isn't detailed in regards to this. I'm not going to spend money if it can't meet my needs, but it's a heck of a lot cheaper than Adobe Professional.

Has anyone navigated the self publishing path in Linux (preferable Ubuntu)? I do have a Windows partition, but really don't like going there. Any suggestions?

---

### Post by sudodus on 2012-12-19
If you are writing something where the editing power of Libre Office is sufficient, you save your original documents in its native format (odt files from Libre Office Writer) and you can export to pdf files directly from Libre Office.

Check if that pdf format is good enough for your purposes :-)

---

### Post by grahammechanical on 2012-12-19
Libreoffice does indeed export as PDF and the help documentation says this:

> **PDF/A-1a**

Converts to the PDF/A-1a format. This is defined as an electronic document file format for long term preservation. All fonts that were used in the source document will be embedded into the generated PDF file. PDF tags will be written.

Export as PDF is in the File Menu.

[http://en.wikipedia.org/wiki/PDF/A]("http://en.wikipedia.org/wiki/PDF/A")

[http://en.wikipedia.org/wiki/PDF/X]("http://en.wikipedia.org/wiki/PDF/X")

[http://en.wikipedia.org/wiki/List_of_PDF_software]("http://en.wikipedia.org/wiki/List_of_PDF_software")

[http://www.scribus.net/canvas/About]("http://www.scribus.net/canvas/About")

[http://wiki.scribus.net/canvas/Help:Manual_PDFx3]("http://wiki.scribus.net/canvas/Help:Manual_PDFx3")

Regards.

---

### Post by Buntu Bunny on 2012-12-19
> **sudodus said:**
> If you are writing something where the editing power of Libre Office is sufficient, you save your original documents in its native format (odt files from Libre Office Writer) and you can export to pdf files directly from Libre Office.

Check if that pdf format is good enough for your purposes :-)

Hi Sudodus. Yes, I've created quite a few pdf files with Libre Office Writer. But I cannot find documentation anywhere about their pdf compliance settings. There is nothing in about it in Libre's pdf options or help files. Since LS is so specific, I suspect not all pdf writers meet their criteria.

---

### Post by Buntu Bunny on 2012-12-19
> **grahammechanical said:**
> Libreoffice does indeed export as PDF and the help documentation says this:

"PDF/A-1a

 Converts to the PDF/A-1a format. This is defined as an electronic document file format for long term preservation. All fonts that were used in the source document will be embedded into the generated PDF file. PDF tags will be written."

Export as PDF is in the File Menu."

Grahammechanical, ok. This is encouraging. I did not find this in the help file but will take a closer look. Sure would be nice to do this without having to spend a bundle.

---

### Post by Buntu Bunny on 2012-12-19
> **grahammechanical said:**
> 

[http://en.wikipedia.org/wiki/PDF/A]("http://en.wikipedia.org/wiki/PDF/A")

[http://en.wikipedia.org/wiki/PDF/X]("http://en.wikipedia.org/wiki/PDF/X")


Ah! And thank you for that!

---

### Post by grahammechanical on 2012-12-19
I have added some more links to my post. You might want to look at Scribus.

Regards

---

### Post by Buntu Bunny on 2012-12-19
> **grahammechanical said:**
> I have added some more links to my post. You might want to look at Scribus.


Grahammechanical, you have been exceedingly helpful and I am most grateful. 

I had Scribus on Lucid, but didn't use it much so I haven't installed on Precise. I will though, because I'm thinking it will probably be more useful for layout work and especially cover design. I think Scribus will be very helpful for all that. Thanks for the suggestion!

---

### Post by Buntu Bunny on 2013-04-26
Well, here's an update (for anyone looking for similar information). Apparently, I do need PDF/X-1a:2001 for professional print-on-demand publishing, not the PDF/A-1a offered by LibreOffice. This appears to be a problem for all self-publishers, since Adobe Acrobat Pro is pretty much the only program that does this. I read one account of another Linux user who was able to create PDF/X-1a:2001 with Scribus v1.5.0. When I looked into that, I discovered it's still in testing, so that's not an option for me (the current version in the repositories, 1.4, doesn't do it). The only other program that seems to create PDF/X-1a:2001 files is Serif PagePlus, at least version 5. This isn't Linux compatible, and in searching the forums it apparently doesn't run under Wine. 

So that's where things stand at the moment. Would appreciate the experience of others in this matter.

---

