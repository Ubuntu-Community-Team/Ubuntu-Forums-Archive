---
title: "Re: OCR software"
date: 2017-04-06
forum: General Help
---

### Post by raleigh3 on 2017-04-06
Is there any OCR software that is fairly reliable in translating an image to text ?

I have to type up documents from a photocopy and boy is it time consuming. :-)

Thanks.

Until I can get my scanner working, any OCR software will not work.

---

### Post by TheFu on 2017-04-06
I've used **gscan2pdf**, but it depends on the quality of the scan and the fonts used in the document. It can be hard-to-impossible to tell the difference between 1, l, i, I, in the different fonts.  Haven't used it with 16.04.

Plus, gscan2pdf is a GUI over about 5 other tools. Those have to be working for it to work.  [http://www.ubuntugeek.com/scan-to-pdf-using-gscan2pdf-in-ubuntu.html](http://www.ubuntugeek.com/scan-to-pdf-using-gscan2pdf-in-ubuntu.html) has install instructions - don't know if those are necessary anymore. Dependencies should be pulled in automatically from the repos by now.  I wouldn't do anything special - a simple apt install and only if that didn't work, would I look for dependency/driver/setup issues for sane/xsane and ghostscript.

So ... the trick for full-text search to work is to put the text *under* the scanned text on the same page.  PDF search will find the correct page, but not be able to highlight the word/line, since it really doesn't know that. After all, the pretty copy is just an embedded image inside the PDF, not text like a generated PDF would create. If you are doing legal documents, you'll want to pay a professional - at least that has been my experience.  For my needs, just getting a few key words spelled correctly and searchable for the page was enough. I didn't need 100% accuracy - or even 80%.

Tables, figures, govt forms/documents, multi-column documents caused the most trouble with the OCR.

Also, I switched from a page scanner to a $50 sheet fed scanner - better speed. It is actually an all-in-one printer/scanner/fax, but after the ink ran out in 2006, I've never used it as a printer again. ;)  Plus I don't have to worry about the huge work scanner/photocopier keeping a copy of every page it ever copied on the internal HDD, unencrypted for the next company, next lease. Very few companies properly destroy/wipe the photocopier 500+ million page buffer when the lease is up.

---

### Post by ^83%u#@^ on 2017-04-07
You can use software like xpdf-utils, programm pdftotext

```
[COLOR=#000000][FONT=&quot]sudo apt-get install xpdf-utils[/FONT][/COLOR]
```[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]
```
[COLOR=#000000][FONT=&quot]pdftotext[/FONT][/COLOR]
```

---

### Post by TheFu on 2017-04-07
**pdftotext** only works with "generated" PDF files, not scanned, image-based, PDF files.  Still, pdftotext is a great tool!

From the manpage:
```
BUGS
       Some  PDF  files contain fonts whose encodings have been mangled beyond
       recognition.  There is no way (short of OCR) to extract text from these
       files.
```

There is also **pandoc**, if you need to convert from different file formats to others.  I love to use it for grabbing webpages and converting to epub or pdf.  It doesn't do OCR either, but does some amazing other things.  I build presentations using pandoc from textile/markdown --> HTML or PDF.

---

### Post by JonPaul on 2017-04-09
Have you tried gimagereader?

---

### Post by raleigh3 on 2017-04-09
I just got to read the messages.

I will report back.

Gscan2pdf did not do well.

The image scanned was real clear text, but it is in boxes.

The boxes may be fooling the software ?

I may trying whiting out those boxes and see if it helps. :-)

> **JonPaul said:**
> Have you tried gimagereader?

gImageReader is a simple GTK+ front-end to tesseract-ocr.

I already have tesseract-ocr.

White out did not help.

I think that if there was only one font available, the software would work fairly well.

When you have many fonts and sizes, and maybe handwriting, and vertical and horiz lines, it's just too much to handle in the programming side.

---

