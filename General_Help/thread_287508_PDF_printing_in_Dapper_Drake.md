---
title: "PDF printing in Dapper Drake?"
date: 2006-10-28
forum: General Help
---

### Post by Takmadeus on 2006-10-28
I have a question:

In Windblows I use a program called PDFcreator in order to print directly from firefox to a PDF file..... I hope you have used this program, if not give it a try (look for it in sourceforge)

Anyway, the thing is that I want to do the same task in ubuntu, so I searched the package list in synaptic and to my surprise I didn't find anything that allows me to do that....

are you kind enough as to compile and upload that package to the repositories?, else, can you tell me how can I print to PDF? (hopefully in a transparent way :))
Thanks in advance

---

### Post by noynac on 2006-10-28
It's not as flexible as PDF Creator, but the following will do the trick:

[http://www.ubuntuforums.org/showthread.php?t=188860&highlight=cups+pdf](http://www.ubuntuforums.org/showthread.php?t=188860&highlight=cups+pdf)

---

### Post by Takmadeus on 2006-10-29
Thanks a lot! trying now and it works ;)

---

### Post by noynac on 2006-10-29
Glad it was helpful. The thanks goes to LoKi128 who wrote the How-To.

BTW, the /etc/cups directory contains a file with the name, cups-pdf.conf, that allows you to set certain options. One is the default directory for the PDF file; a second option is to preface the PDF file name with a job id (so that existing PDF files are not overwritten.

---

### Post by Takmadeus on 2006-10-31
I'll check it out later... but so far has givn astonishing results.... image quality is quiyte good IMO, so I think I will stick to the default options.... yet, I would like to know who is in charge of mantaining that package... that's because I wonder if it would be possible to make cups-pdf (the binary) suid already, or just accesible without having to change permissions, plus, if it would be possible to add a little interface to configure some stuff (/etc/cups/cups-pdf.conf) Just a suggestion from an end user ;)

---

