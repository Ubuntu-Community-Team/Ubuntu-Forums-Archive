---
title: "PDF conversion"
date: 2013-02-21
forum: General Help
---

### Post by kr651129 on 2013-02-21
Not really an Ubuntu question, but I always find good answers here.  I have an existing PDF that I want to regenerate with different encoding.  I cant find any way to do this with iText.  Has anyone here had any experience with this?

---

### Post by Impavidus on 2013-02-21
I've never changed encodings in pdfs (prefering to do it before converting to pdf), but I have some experience with font encoding in postscript (the more complex predecessor of pdf, designed to be human readable, in addition to being Turing complete). So let me get this straight.

We're talking about font encoding. The pdf contains text as a compressed series of bytes. A font, often but not always embedded in the pdf, contains the encoding vector or refers to a standard one, converting numbers into names of characters. The glyph dictionary then converts the character names into graphical descriptions. And you want to modify the encoding table? Is the purpose to replace one character by an alternative one also present in the font? Or replace the font by one using a different encoding table? But then you would try to replace the entire font. Or has somehow the wrong encoding vector crept into the font?

There may be some tool available. I'm not sure I can help you, but my curiousity was awoken.

---

### Post by thnewguy on 2013-02-21
I don't know about changing the PDF directly, but I use Able2Extract which lets me convert the PDF into an office document (MS-Office and LibreOffice formats are supported) and then you can make changes and save those files back to PDF format.

---

### Post by conradin on 2013-02-21
You could try printing to a file. EOG lets you print to post script, or svg. If you give a specific encoding type perhaps you can get better answers.

---

