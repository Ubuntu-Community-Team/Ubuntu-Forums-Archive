---
title: "pdftotxt"
date: 2013-09-13
forum: General Help
---

### Post by Mariane on 2013-09-13
Please, does someone know where the packages pdftotxt or pdf2txt have gone to? Or what is available to extract text from a pdf file?
And what does "linearized PDF" mean?

---

### Post by vasa1 on 2013-09-13
Did you try "pdftotext" instead of pdftotxt or pdf2txt? No idea about linearized pdf. Anyone?
From `man pdftotext`:
```
NAME
       pdftotext - Portable Document Format (PDF) to text converter (version 3.03)

SYNOPSIS
       pdftotext [options] [PDF-file [text-file]]

DESCRIPTION
       Pdftotext converts Portable Document Format (PDF) files to plain text.

       Pdftotext reads the PDF file, PDF-file, and writes a text file, text-file.  If text-file is not specified, pdftotext converts file.pdf to file.txt.  If text-
       file is ´-', the text is sent to stdout.

```

And, from wikipedia ([http://en.wikipedia.org/wiki/Portable_Document_Format):](http://en.wikipedia.org/wiki/Portable_Document_Format):)
> There are two layouts to the PDF files&#8212;non-linear (not "optimized") and linear ("optimized"). Non-linear PDF files consume less disk space than their linear counterparts, though they are slower to access because portions of the data required to assemble pages of the document are scattered throughout the PDF file. Linear PDF files (also called "optimized" or "web optimized" PDF files) are constructed in a manner that enables them to be read in a Web browser plugin without waiting for the entire file to download, since they are written to disk in a linear (as in page order) fashion.[11] PDF files may be optimized using Adobe Acrobat software or QPDF.

And `qpdf` is available from the software center.

---

### Post by Mariane on 2013-09-15
Thank you very much. So "linearized" has no consequence over converting to txt? 

I tried pdftotxt. It has no man entry on my computer. If I simply type
```

pdftotxt

```
I get:
```

No command 'pdftotxt' found, did you mean:
 Command 'pdftotext' from package 'poppler-utils' (main)

```
So I tried 
```

sudo apt-get install poppler-utils

```
But the answer was:
```

poppler-utils is already the newest version.

```

I also tried to find it "manually", with:
```

cd /
sudo find ./ -name pdftotxt

```
because I thought it could be an issue with $PATH. But nothing was found. 

(I search as root, to avoid getting all the "permission denied" messages which otherwise fill up the screen.)

---

### Post by vasa1 on 2013-09-15
It's pdftot**_e_**xt, not pdftotxt.

---

