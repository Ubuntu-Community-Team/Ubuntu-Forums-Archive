---
title: "Print documents to eps files"
date: 2012-10-16
forum: General Help
---

### Post by papa33170 on 2012-10-16
Hi,

I would like to print libreoffice documents (spreadsheets) to .eps (.png would do the trick also) files, in order to put them into a LaTeX file. 
For the moment, I export the spreadsheet to pdf and then select the corresponding area
in the pdf file to export it to a png file, but the result is not very good.
So basically I need a virtual printer to produce eps ot png files, but I haven't found something like this yet.

Thanks in advance for answering.

---

### Post by LewisTM on 2012-10-16
You can do that in a few easy steps.
1) Open the Print dialog and set the page to be exported. 
2) Click the Properties button -> Device Tab -> Printer Language type -> PostScript (Level from driver)
3) Click OK. Back in the Print Dialog, go to Options tab -> Check Print to file
4) Click Print to File... at the bottom and choose a filename.ps

To convert that ps to **eps**, execute
```
ps2eps <file name>
```
To convert to **png**, install the imagemagick package and run
```
convert output.ps output.png
```
Run [FONT="Courier New"]man convert[/FONT] to know more about the various options for conversion.

Cheers!

---

### Post by papa33170 on 2012-10-16
Thank you for your answer! Works like a charm!

---

### Post by LewisTM on 2012-10-16
Glad to be of service. Please mark as SOLVED.

---

