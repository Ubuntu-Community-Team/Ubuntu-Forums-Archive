---
title: "Software suggestions: Scan + Pdf + OCR = Searchable pdf?"
date: 2008-02-25
forum: General Help
---

### Post by dmitrijledkov on 2008-02-25
I can scan into pdf's just fine. Thanks a lot everyone!

But I want to challenge ubuntu for the my beloved feature of Adobe Acrobat Pro (I think standard as well):

It can do OCR on scanned pdf to make it a searchable pdf (i.e. exactly as regular ones).

Any suggestions on achieving this without booting back to mac os x? Cause this is about last feature I still dual boot for =D.

Thanks a lot and keep up the good work everyone!

---

### Post by MAMdk on 2008-03-10
I have thought of this too, only reason that I keep my old windows box ... 
I have a HP PSC with bundled software to do searchable PDFs, but ofcourse it won't work in wine.

---

### Post by astrotech226 on 2008-03-10
Have you looked into Tesseract?  It works pretty well, but it runs from the command line.  A script could automate a lot of this.  You have to convert the PDF to a tiff file, run it through tesseract, then convert from the text file back to a pdf.  The core use of Tesseract is like this:

```
tesseract testfile.tif outfile
```

You end up with three files, one called outfile.txt.  You can delete the other two.

---

### Post by dmitrijledkov on 2008-03-11
> **astrotech226 said:**
> 

You end up with three files, one called outfile.txt.  You can delete the other two.

I know about this program to do OCR to get the test out. My wish is to end up with the same pdf in terms of looks but with ability to use search function in my pdf viewer to find words and or use indexing search engine on those pdfs.

In the other words something to give scanned pdf behaviour similar to computer generated pdf.

---

