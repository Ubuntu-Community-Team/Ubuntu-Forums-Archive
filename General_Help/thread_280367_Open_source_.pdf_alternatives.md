---
title: "Open source .pdf alternatives?"
date: 2006-10-19
forum: General Help
---

### Post by ebeyer on 2006-10-19
In advocating for open source alternatives to proprietary file
formats (eg, MS Word .doc,  MS Excel .xls --> .odw, .ods) I'm 
having a hard time finding a real alternative to Adobe .pdf.  
That may be because I am so new to the concept of open source
software in general.

Is there such an open source alternative?  Can somebody point 
me to a link that would explain this in some detail?

Many advance thanks,

ebeyer

---

### Post by metalheart on 2006-10-19
PDF is open standard. Acrobat is not OSS.

---

### Post by taurus on 2006-10-19
You have xpdf, gpdf, gv, etc.  You don't have to use Adode Acrobat to read pdf files...  You can install them from repos.

---

### Post by ebeyer on 2006-10-19
Right, but that's open source **software** reading proprietary files, like .mp3.  I'm looking for an open source **file format**, like ogg vorbis.

Thanks.

---

### Post by ebeyer on 2006-10-19
Oh.  So .pdf is an open standard?  That settles that, then.  Thanks.

EB

---

### Post by DarkN00b on 2006-10-19
You can create PDFs with Open Office.org word processor...

---

### Post by MWAAAHAAA on 2006-10-19
Postscript or DVI (device independent) is what you are looking for. DVI is output by the TeX typeset program (tetex package in ubuntu). This can then be converted to postscript. Especially the former may be interesting to you. Postscript can be viewed using ghostview.

For anyone who might think that PDF is free I suggest to read up on the topic. Here an excerpt from wikipedia [link]http://en.wikipedia.org/wiki/Pdf[/link]: > Anyone may create applications that read and write PDF files without having to pay royalties to Adobe Systems; Adobe holds a number of patents relating to the PDF format but licenses them on a royalty-free basis for use in developing software that complies with its PDF specification.[1]

---

### Post by FrankVdb on 2006-10-20
That does make the pdf format free, doesn't it? Not open source, but free nevertheless.

---

### Post by M7S on 2006-10-20
The only restriction is that you cant fork it, right? IMHO that's not too bad even if it doesn't go too well with FSF's freedom 3.

---

### Post by anaconda on 2006-10-20
> **M7S said:**
> The only restriction is that you cant fork it, right? IMHO that's not too bad even if it doesn't go too well with FSF's freedom 3.

That is just good, because it means that microsoft cant "add" features to pdf, and force everyone to use microsofts version of pdf..  and making the orginal pdf useless in the long run..

M$ is famous of this kind of attacks..

---

### Post by MWAAAHAAA on 2006-10-20
> **FrankVdb said:**
> That does make the pdf format free, doesn't it? Not open source, but free nevertheless.

Depends on your definition of free. It does not fit mine, and neither does it fit GNU's.

---

### Post by almahtar on 2006-10-20
To answer the question of the original poster, PDF is proprietary like .mp3.  The other poster's suggestion to use Postscript/TeX (my favorite flavor of which is LaTeX) is to my knowlege the best free (as in speech) alternative to PDF.

The PDF is an open standard (not source, for those of you talking about forking), but the patents it relies on are the property of Adobe.  At the moment it allows their use free (as in beer), but that does not make PDF free (as in speech).  It is still proprietary.

---

