---
title: "How to add a signature to a PDF"
date: 2013-11-30
forum: General Help
---

### Post by JR_UB on 2013-11-30
I am looking for a way to annotate a PDF file with the image of a signature, then save it as one merged document.  I'm hoping to get some suggestions here on an way way to do this. In a windows environment I used to use Nitro PDF but I can't get it to run on Ubuntu with wine.

---

### Post by howefield on 2013-11-30
LibreOffice Draw should accommodate you.

---

### Post by vanadium on 2013-11-30
I suggest xournal.

---

### Post by ajgreeny on 2013-11-30
You could also open the PDF with gimp and then add your signature.  Finally print to file as PDF again.

---

### Post by Impavidus on 2013-11-30
Gimp may convert the entire document to raster format instead of vector format, which is probably not what you want.

I think inkscape can do things like this quite well.

---

### Post by ajgreeny on 2013-12-01
> **Impavidus said:**
> Gimp may convert the entire document to raster format instead of vector format, which is probably not what you want.

I think inkscape can do things like this quite well.

Showing my ignorance here, but does that matter if the OP needs a PDF file at the end?  I note he wants **"one merged document"** at the end, and of course, that could be almost any file type, but I assumed a PDF was wanted.

---

### Post by Impavidus on 2013-12-01
PDF is a vector format, which can contain objects like text, vector drawings and raster images. Unless it was recently changed (I'm using the default gimp in 12.04), gimp will save any PDF as a file containing only one object, being a large raster image. Any text in the original PDF will be rasterised and stored in that way (as an image, not as text), reducing image quality and increasing file size. I assumed the OP has a PDF containing mostly vector data, like text. The best way seems to me to add the raster image of the signature as a new object to the PDF, without modifying the data already present. Several tools can do so, but I don't think gimp can.

---

### Post by vanadium on 2013-12-01
That is where current versions of xournal do a good job. It preserves the content of the PDF, but adds a layer with the signature (or other text, graphics, annotations ...).

An alternative way would be to create a blank page with the signature, and then "stamp" this on the PDF with pdftk.

Inkscape may indeed also be suited for this. I do not have experience withit for this purpose, though.

---

### Post by vanadium on 2013-12-01
Inkscape "imports" the PDF, and thus may introduce changes and artefacts. In a small test file, a horizontal line was not imported. xournal, on the other hand, will preserve the data of the original PDF as is.

---

### Post by JR_UB on 2013-12-01
For clarity, I did want a PDF at the end.  I tried a few of these and found xournal to perfrom for my purpses

---

### Post by ajgreeny on 2013-12-01
> **JR_UB said:**
> For clarity, I did want a PDF at the end.  I tried a few of these and found xournal to perfrom for my purpses

Thank you for the comment on your success; it is just what is often missing after different answers have been given to a question so it's terrific to get an answer that we know works.

I do see, however, that xournal files are not PDFs and can not be opened with a PDF reader like evince.  Is it possible to save a xournal file as a PDF?

EDIT: Nevermind, I have just noticed that there is an option to export as PDF after adding something to the original PDF file.

---

### Post by vanadium on 2013-12-04
Previous versions would export annotated PDF's as a graphic (in a PDF). With current versions, the vectordata of the original PDF (and thus the quality) appear to be preserved, and your annotations added on an additional layer. Nice.

---

