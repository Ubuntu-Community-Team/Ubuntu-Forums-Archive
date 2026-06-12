---
title: "pdftk bursts single PDF documents into larger file size pages"
date: 2008-04-20
forum: General Help
---

### Post by figo2476 on 2008-04-20
Hi:

I realize that pdftk bursts single PDF documents into larger file size pages. Each individual files are added up > the original PDF file. Is there any way to work around?

---

### Post by niteshifter on 2008-04-21
Hi,

Not really. Each page-document is a complete, new pdf document with a description of the page (size / format), fonts, etc.

---

### Post by figo2476 on 2008-04-21
Because I burst a 2mb PDF file, into single pdf files. Then I reorder some pages and merge back. It becomes 25mb and it is not acceptable. Is there any way I can reduce the size or something else

---

### Post by vanadium on 2008-04-21
I confirm this issue. However, when using ghostscript to combine the files, I ended up with a small file again (3.5 MB rather than 3.4 MB).

gs -dBATCH -dNOPAUSE -q -sDEVICE=pdfwrite -sOutputFile=0_test_gs.pdf pg*

(where pg* represents all the pages produced by pdftk). The processing was slightly long and gs continuously complained in the sense of:

```

   **** Warning:  File has an invalid xref entry:  2.  Rebuilding xref table.

   **** Warning: Fonts with Subtype = /TrueType should be embedded.
                 The following fonts were not embedded:
                        TimesNewRomanPS-BoldMT

   **** This file had errors that were repaired or ignored.
   **** The file was produced by: 
   **** >>>> itext-paulo-155 (itextpdf.sf.net-lowagie.com) <<<<
   **** Please notify the author of the software that produced this
   **** file that it does not conform to Adobe's published PDF
   **** specification.


```

---

### Post by figo2476 on 2008-04-21
Hi:

Thank you for the reply. I am not very familiar with gs. So I wonder whether you can burst PDF document with gs (to get rid of errors). Also I think pdfwrite is the device to output pdf file. I wonder if it uses other devices will get rid of the errors.

---

### Post by noynac on 2008-04-22
@vanadium. 

Thanks for the suggested command line. I combine PDF files on a regular basis and ghostscript does seem to create smaller files in many instances. Also, ghostscript has many useful options not present in PDFtk. 

As to error messages, you can suppress many of these by appending 2>/dev/null to the end of the command line.

@figo2476.

You can extract out a page or consecutive pages with ghostscript with the following command line:

gs -sDEVICE=pdfwrite -dNOPAUSE -dQUIET -dBATCH \
-dFirstPage=m -dLastPage=n -sOutputFile=out.pdf in.pdf

[http://centaur.maths.qmw.ac.uk/Info/pdf-faq.html](http://centaur.maths.qmw.ac.uk/Info/pdf-faq.html)

Other than repeatedly using the above command line, there does not appear to be any way to burst an existing PDF file into individual pages using ghostscript:

*Specifying a single output file works fine for printing and rasterizing figures, but sometimes you want images of each page of a multi-page document. You can tell Ghostscript to put each page of output in a series of similarly named files.... Note however that the one page per file feature is not supported by all devices; in particular it does not work with document-oriented output devices like pdfwrite and pswrite.*

[http://pages.cs.wisc.edu/~ghost/doc/cvs/Use.htm#Help_command](http://pages.cs.wisc.edu/~ghost/doc/cvs/Use.htm#Help_command)

---

### Post by figo2476 on 2008-04-30
update:

gs -dBATCH -dNOPAUSE -q -sDEVICE=pdfwrite -sOutputFile='/var/www/test/test.pdf' "/var/www/1.pdf" "/var/www/2.pdf" .....

1.pdf, 2.pdf, etc are pdf files split by pdftk. The output is 1 single file with 1 blank page (6k). There is something wrong and I  am not sure why


I got an email from the author of pdftk. He says the issue is fixed since 1.4. I tried it, but 5mb produces 25mb file

---

### Post by figo2476 on 2008-04-30
#gs -dBATCH -dNOPAUSE -q -sDEVICE=pdfwrite #-sOutputFile='/var/www/test/test.pdf' "/var/www/1.pdf" #"/var/www/2.pdf" .....

#1.pdf, 2.pdf, etc are pdf files split by pdftk. The output is 1 #single file with 1 blank page (6k). There is something wrong and I #am not sure why

Regarding to this, it gives error "Unable to open the initial device, quitting." while I run it on command line.

I assume ghostscript 7 on the CentOS is a bit old and I will upgrade to version 8.

---

