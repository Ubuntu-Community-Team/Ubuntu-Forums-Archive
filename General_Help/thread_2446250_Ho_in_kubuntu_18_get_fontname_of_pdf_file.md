---
title: "Ho in kubuntu 18 get fontname of pdf file ?"
date: 2020-06-27
forum: General Help
---

### Post by petrogromovo on 2020-06-27
[COLOR=#000000]Hello,[/COLOR][COLOR=#000000]
I have a pdf file, if there is a way [/COLOR][COLOR=#000000]in kubuntu 18 
to get fontname, size, weight in any part of this pdf file ?[/COLOR][COLOR=#000000]
I have okular installed, but I did not find how to get this info...

[/COLOR][COLOR=#000000]Thanks![/COLOR]

---

### Post by lvm on 2020-06-27
Open in in libreoffice. It converts pdfs to draw, so it will be awkward, but you'll get what you want.

---

### Post by TheFu on 2020-06-27
The way that the PDF was created matters. Many are just scanned images. If that is the situation, there won't be any useful font names.
However, if the PDF was created from a text-based source, then the font may be embedded in the file. At the creation time, the PDF author can choose to include all fonts, no fonts, or unpopular fonts hoping that the reader's system has the most popular fonts installed already.

For example:
```
$ strings The_Linux_Command_Line-William_Shotts_1364.pdf |egrep FontName |more
<</Type/FontDescriptor/FontName/EAAAAA+DejaVuSans
<</Type/FontDescriptor/FontName/BAAAAA+LiberationSans-Bold
<</Type/FontDescriptor/FontName/KAAAAA+OpenSymbol
<</Type/FontDescriptor/FontName/NAAAAA+LiberationMono-BoldItalic
<</Type/FontDescriptor/FontName/DAAAAA+LiberationSerif
<</Type/FontDescriptor/FontName/FAAAAA+LiberationSerif-Bold
<</Type/FontDescriptor/FontName/JAAAAA+LiberationMono
<</Type/FontDescriptor/FontName/GAAAAA+LiberationSans-BoldItalic
<</Type/FontDescriptor/FontName/HAAAAA+LiberationSans-Italic
<</Type/FontDescriptor/FontName/LAAAAA+LiberationMono-Bold
<</Type/FontDescriptor/FontName/IAAAAA+LiberationSerif-Italic
<</Type/FontDescriptor/FontName/CAAAAA+LiberationSans
<</Type/FontDescriptor/FontName/OAAAAA+LiberationSerif-BoldItalic
<</Type/FontDescriptor/FontName/MAAAAA+LiberationMono-Italic
```
and for a mostly scanned file:
```
$ strings  xyz.pdf |egrep FontName
/FontName /PDYGRV+Frutiger-Black
/FontName /PDYGRV+Frutiger-Roman
/FontName /PDYGRV+Utopia-Regular
```

You can clean up the font names with a little **sed** or **perl**, pretty easily.

---

