---
title: "Rotating PDF's permanently"
date: 2013-04-03
forum: General Help
---

### Post by blanka32 on 2013-04-03
Hey guys, at the office were having a hard time with some of our PDF files. Were
converting multiple scanned images into a single PDF but they are all coming out 
sideways, and i'm havin a hard time finding a program that will rotate the files 
and save as *permanently.  *I've tried PDF X-Change, nitro reader, adobe acrobat
(we don't have a paid account anymore and its not looking like an option for the
foreseeable future). I'm using ubuntu on my laptop but all the rest of the office 
computers are on windows, so if there could be an open source option that supplies
for both as far as rotating and saving PDF files permanently, that'd be awesome, 
I'm just having a hard time finding anything through google atm. 

-Regards

---

### Post by SeijiSensei on 2013-04-03
I bet you can do it with [Imagemagick convert]("http://www.imagemagick.org/script/convert.php").  It's a command-line program that knows how to handle PDF files as well as many other formats.  You can install it from the repositories with "sudo apt-get install imagemagick".  It could be as simple as 

```
convert input.pdf -rotate 90 output.pdf
```

---

### Post by blanka32 on 2013-04-03
> **SeijiSensei said:**
> I bet you can do it with [Imagemagick convert]("http://www.imagemagick.org/script/convert.php").  It's a command-line program that knows how to handle PDF files as well as many other formats.  You can install it from the repositories with "sudo apt-get install imagemagick".  It could be as simple as 

```
convert input.pdf -rotate 90 output.pdf
```

thanks. I'm going to check that one out. 

any programs out there for both platforms?

---

### Post by slickymaster on 2013-04-03
[ePDFView]("http://freecode.com/projects/epdfview") is a lightweight PDF document viewer that only uses the GTK+ and Poppler libraries. It has the standard tools such as: Next/Previous page, Zoom in/out, enter a page number manually, full screen view, a text selector, Rotate pages Right & Left, Save as a copy, Search for text, Send to Print.
```
sudo apt-get install epdfview
```

---

### Post by vanadium on 2013-04-03
Evince does that also. That is not what the OP is looking for.

I am not sure whether the "convert" option does not also change the actual data contained in the PDF (e.g. rasterizing) besides just rotating it. If it doesn't, then indeed that is a fast and elegant solution using software that is standard in the system. I did a test drive, and indeed, a 430 kb pdf came out as a 1.3 MB rotated PDF, all rasterized in poor resolution. So that is not an option.

Probably one can achieve this using ghostscript, but more convenient is pdftk. There are also some "graphical" solutions in the software center: just search for "PDF".

---

### Post by cathyhill on 2014-01-06
Read this article

[http://www.codeproject.com/Tips/223368/How-to-Permanently-Rotate-a-PDF-file](http://www.codeproject.com/Tips/223368/How-to-Permanently-Rotate-a-PDF-file)

> **blanka32 said:**
> Hey guys, at the office were having a hard time with some of our PDF files. Were
converting multiple scanned images into a single PDF but they are all coming out 
sideways, and i'm havin a hard time finding a program that will rotate & [[COLOR=#272727]read PDF[/COLOR]]("http://www.rasteredge.com/how-to/asp-net-imaging/pdf-reading/") the files 
and save as *permanently. *I've tried PDF X-Change, nitro reader, adobe acrobat
(we don't have a paid account anymore and its not looking like an option for the
foreseeable future). I'm using ubuntu on my laptop but all the rest of the office 
computers are on windows, so if there could be an open source option that supplies
for both as far as rotating and saving [[COLOR=#272727]PDF[/COLOR]]("http://www.rasteredge.com/formats/pdf/")[COLOR=#272727] [/COLOR]files permanently, that'd be awesome, 
I'm just having a hard time finding anything through google atm. 

-Regards

---

### Post by harishcm-pals on 2014-03-20
I think the best tool for this purpose would be pdftk.

The code goes like this: pdftk <input filename> cat <page range><rotation> output <output filename>

So, to rotate only page 7 of in.pdf 90 degrees clockwise:

```

pdftk in.pdf cat 1-6 7E 8-end output out.pdf

```

To rotate the entire document in.pdf by 180 degrees:

```

pdftk in.pdf cat 1-endS output out.pdf

```

---

