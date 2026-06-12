---
title: "Problem with printing Open Office document to PDF"
date: 2013-04-12
forum: General Help
---

### Post by SillySod on 2013-04-12
I've got a set of documents in Open Office format which I need to export to PDF for printing.  I've tried several methods - ticking the "print to file" option under my normal printer, using the CUPS-PDF printer and also using the Open Office "export to PDF" option, but the same problem occurs each time.

It's this: most of the text is black but some of it is coloured.  The coloured text always comes out black in the PDF.  The rest of the colours in the background image and embedded pictures are fine, it's just the text which I have put in colour which doesn't work.

The colour I have used is a special colour which I have mixed from the palette myself, could that be the problem?

---

### Post by Vaphell on 2013-04-12
how did you manage to customize that color? I don't see it anywhere in both libre office and open office, i only get predefined lists of colors.

edit: ok, i've found it, in tools > options > colors you can add new colors to the list

export to pdf works just fine

---

### Post by SillySod on 2013-04-13
I've got a bit further in finding a solution.

It turns out that the machine I have which is running Ubuntu 12.04 actually has "Libre Office 3.5.7.2", and no matter what I try - export to PDF, print to PDF printer, print to file, the coloured text comes out in black in the PDF.

However, using my other machine running Ubuntu 10.04 and OpenOffice 3.2, I can use the "export to PDF" option and the text comes out in the correct colour.  Still on this machine, using any kind of PDF printer gives black.

So it sounds like antiquity triumphs over progress as always!

I could do with this problem being fixed on Libre Office/Ubuntu 12.04 though, it's a bit inconvenient to have to do the PDF creation on a completely different machine to the one I'm writing the text on!  Could it be that the bright sparks have set a default option to always print text in black when a PDF is created?

---

### Post by Hagar Delest on 2013-04-14
You can remove LibreOffice and install AOO: [[Ubuntu] Installing OOo on Debian and Co.](http://forum.openoffice.org/en/forum/viewtopic.php?f=16&t=68).
NB: once installed with the .debs, you can also reinstall LibreOffice but with the .debs from their site too.

---

### Post by Vaphell on 2013-04-14
I don't have printer so no idea about the printing but i checked 'export to pdf' in 12.04 (virtualbox), in 13.04 (vb) and in open office in 10.04 (my main system). In all cases pdf file shows proper custom color.

---

### Post by cwsnyder on 2013-04-14
If your 'custom color' is being interpreted by the PDF export function as too near the HTML link color, it may automatically print it in black, as the link is broken if the linked-to text is not in the printed document.  The newer ODT and DOCX format files are actually compressed HTML files, which may be tripping you up.

---

### Post by cathyhill on 2013-12-04
> **SillySod said:**
> I've got a set of documents in Open Office format which I need to export to [[COLOR=#272727]PDF[/COLOR]]("http://www.rasteredge.com/dotnet-imaging/addon-pdf-document-generator/") for printing.  I've tried several methods - ticking the "print to file" option under my normal printer, using the CUPS-PDF printer and also using the Open Office "export to PDF" option, but the same problem occurs each time.

It's this: most of the text is black but some of it is coloured.  The coloured text always comes out black in the PDF.  The rest of the colours in the background [[COLOR=#272727]image[/COLOR]]("http://www.rasteredge.com/dotnet-imaging/features.shtml") and embedded pictures are fine, it's just the text which I have put in colour which doesn't work.

The colour I have used is a special colour which I have mixed from the palette myself, could that be the problem?


I do not think it is related to the special color that you mixed by yourself. And you can vertify this by using a common color. Here is a similar issue on print colorful text in gray using OO.

[https://forum.openoffice.org/en/forum/viewtopic.php?f=5&t=54739](https://forum.openoffice.org/en/forum/viewtopic.php?f=5&t=54739)

---

