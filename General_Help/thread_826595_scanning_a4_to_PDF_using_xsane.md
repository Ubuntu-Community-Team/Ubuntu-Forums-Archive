---
title: "scanning a4 to PDF using xsane"
date: 2008-06-12
forum: General Help
---

### Post by McHenry on 2008-06-12
I regularly scan documents to either archive, email or fax and my usual scanner has gone to god. I am using my backup Canon Lide 20 A4 flatbed scanner however when I scan an A4 document the resultant PDF size is approx 2mb and I cannot work out how to make it small like the files my other scanner created. When some docs are 30+ pages long you really notice the file size difference.

Thanks

McHenry

---

### Post by McHenry on 2008-06-12
For example I just scanned a 35 multipage doc to both ps and pdf.

Both files are 65.5 mb in size which is ridiculous.

I have converted the ps doc to pdf using ps2pdf and the file size is only 8.3 mb which is acceptable.

Something must be wrong with the xsane compression settings.

---

### Post by komputes on 2008-06-12
I think ps is uncompressed. Although you save a scan as a pdf I think it is in fact a ps file. Could this be the case?

---

### Post by McHenry on 2008-06-12
OK, that makes sense...

So an xsane PDF is an uncompressed PS. Would there be any way to make the xsane PDF compressed without having to save it to PS then running it through ps2pdf ?

---

### Post by komputes on 2008-06-12
Well the way I see it is that it's not a PDF at all. Even with PDF extension, if I send it to a Mac client, they only see it it if the extension is changed to PS. As well, I use xsane through GIMP and GIMP doesn't let me save as PDF as far as I know, so I think it's a PS which is not compressed for portability masquerading as a PDF.

---

### Post by kaibob on 2008-06-12
> **komputes said:**
> Well the way I see it is that it's not a PDF at all. Even with PDF extension, if I send it to a Mac client, they only see it it if the extension is changed to PS. As well, I use xsane through GIMP and GIMP doesn't let me save as PDF as far as I know, so I think it's a PS which is not compressed for portability masquerading as a PDF.

You can check a PDF file with the pdfinfo commandline utility. I believe it's included with a standard Hardy install. The command is:

```
pdfinfo PDFfilename
```

As an aside, I ran a test in which I created a PS file with the Firefox print-to-file option; gave this file a PDF extension; and then tried to obtain information about that file with the pdfinfo utility. I received the following:

```
Error: May not be a PDF file (continuing anyway)
Error: PDF file is damaged - attempting to reconstruct xref table...
Error: Couldn't find trailer dictionary
Error: Couldn't read xref table
```

---

### Post by McHenry on 2008-06-13
mchenry@laptop:~$ ls -l xsane_test*.*
-rw-r----- 1 mchenry mchenry 68740719 2008-06-12 17:42 xsane_test.pdf
-rw-r----- 1 mchenry mchenry 68732078 2008-06-12 17:39 xsane_test.ps

mchenry@laptop:~$ ps2pdf xsane_test.ps xsane_test_2.pdf
warning: ignoring zlib error: incorrect data check
warning: ignoring zlib error: incorrect data check
warning: ignoring zlib error: incorrect data check
warning: ignoring zlib error: incorrect data check
warning: ignoring zlib error: incorrect data check
warning: ignoring zlib error: incorrect data check
warning: ignoring zlib error: incorrect data check
warning: ignoring zlib error: incorrect data check
warning: ignoring zlib error: incorrect data check
warning: ignoring zlib error: incorrect data check
warning: ignoring zlib error: incorrect data check
warning: ignoring zlib error: incorrect data check
warning: ignoring zlib error: incorrect data check
warning: ignoring zlib error: incorrect data check
warning: ignoring zlib error: incorrect data check
warning: ignoring zlib error: incorrect data check
warning: ignoring zlib error: incorrect data check
warning: ignoring zlib error: incorrect data check
warning: ignoring zlib error: incorrect data check

mchenry@laptop:~$ ls -l xsane_test*.*
-rw-r--r-- 1 mchenry mchenry  8686240 2008-06-13 20:51 xsane_test_2.pdf
-rw-r----- 1 mchenry mchenry 68740719 2008-06-12 17:42 xsane_test.pdf
-rw-r----- 1 mchenry mchenry 68732078 2008-06-12 17:39 xsane_test.ps

mchenry@laptop:~$ pdfinfo xsane_test_2.pdf
Producer:       GPL Ghostscript SVN PRE-RELEASE 8.61
CreationDate:   Fri Jun 13 10:51:25 2008
ModDate:        Fri Jun 13 10:51:25 2008
Tagged:         no
Pages:          35
Encrypted:      no
Page size:      595 x 842 pts (A4)
File size:      8686240 bytes
Optimized:      no
PDF version:    1.4

mchenry@laptop:~$ pdfinfo xsane_test.pdf
Title:          XSane scanned image
Creator:        XSane version 0.991 (sane 1.0) - by Oliver Rauch
Producer:       XSane 0.991
CreationDate:   Thu Jun 12 07:42:18 2008
Tagged:         no
Pages:          35
Encrypted:      no
Page size:      594 x 835 pts
File size:      68740719 bytes
Optimized:      no
PDF version:    1.4

mchenry@laptop:~$ pdfinfo xsane_test.ps
Error: May not be a PDF file (continuing anyway)
Error: PDF file is damaged - attempting to reconstruct xref table...
Error: Couldn't find trailer dictionary
Error: Couldn't read xref table

---

