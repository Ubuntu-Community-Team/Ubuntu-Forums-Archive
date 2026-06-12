---
title: "pandoc pdf convertion to markup"
date: 2019-10-01
forum: General Help
---

### Post by Drenriza on 2019-10-01
Hi all!

Pandoc is a fantastic tool to convert between different formats, but i cant quite seem to figure out how i can convert a existing pdf document to markup.
Anyone has an idea how this can be done?

Thanks in advance
Best regards

---

### Post by dragonfly41 on 2019-10-01
I don't see a pdf to markdown option (usually it is the reverse .. md to pdf) but there is some [discussion here]("https://groups.google.com/forum/#!msg/pandoc-discuss/8qm82cPRGnU/QUro0yaMAAAJ").

---

### Post by Holger_Gehrke on 2019-10-01
According to pandoc.org it's not possible to read pdf, only writing is supported. You could try pdftohtml from the package poppler-utils to first convert to html and go on from that, but thanks to the nature of pdf the results of that conversion are often not very useful. pdf is more concerned with exact reproduction of the intended appearance of a document than with it's logical structure. At heart it's a multi-page vector graphics format with the abilities to also contain bitmaps and text.

Holger

---

### Post by TheFu on 2019-10-01
There is also **pdftotext**.

But as others have said, PDF is all about page layout. Many PDF files are simply scanned images shovelled into a PDF "container". Those cannot be trivially converted into text without using OCR.  It really comes down to how the PDF file was created.  If someone uses a word processor to make a PDF file, then there is a good chance it can be converted to text.  But if the PDF file has multiple columns, that text will be jumbled - think top-left to lower-right reading where the fact that there are columns is unknown to the conversion tool.
Plus PDF is based on postscript which can include user-defined fonts. To PDF, these are just little glyphs, not a letter. When converting to text, glyphs could be ignored completely, like any images.

You'll never know how a file might convert until you try.  If you find it is an image-based PDF, you might try some OCR and get lucky enough. Just depends on how clean the scan is.  **gscan2pdf** has an OCR capability which might be useful.  It is really a front end to a scanner that also will do OCR and store any text _under_ the image displayed.  This makes full text searching work for the PDF which can be extremely useful.  I've found the OCR to be about 90% accurate, which isn't really sufficient, but as long as some keywords for the page are correct, full text searching will work and display the correct page.

---

### Post by Drenriza on 2019-10-02
Thanks for the replies all.
I can tell its not as cut and dry as i thought.

I thought that a pdf document had a "fixed" setup that could be translated to anything else.
But that does not seem to be the case :)

---

