---
title: "How do I Convert a PDF to SVG for Inkscape"
date: 2007-02-06
forum: General Help
---

### Post by charlie. on 2007-02-06
I have a PDF file with a single page containing vector graphics. This page contains loads of cruft and a small, highly-detailed graphics (a map of a campus) in the corner. I want to remove the cruft and print only this map. Better still, this map is a vector graphics so I should be able to expand it to exploit the free space.

One way to do this would be to open the PDF file in a vector graphics program, like Inkscape, delete the cruft and scale up the map. There's only one problem. Inkscape won't load a PDF file.

How do I convert the PDF file into a format that Inkscape can read, ideally SVG?

I have tried GhostScript, and managed to convert it into a Postscript (.ps) file. This is not very useful.

I pushed the Postscript file through a utility called "ps2eps" and created an EPS file, thinking that Incscape would be able to read that, but Inkscape cannot read EPS files. It cannot import them either, despite what the documentation says.

I tried a utility called "pstoedit" and, with the following command...

```
pstoedit -f plot-svg NMMU.pdf NMMU.svg
```

... I managed to create an SVG file. This file DID load in Inkscape, but it displays tons of graphics corruption - i.e. things that should NOT be filled are filled with black - including the bodies of letters like 'D'. (You guessed it, this is not useful.)

I am out of ideas. Please help.

---

### Post by mightyteegar on 2007-02-06
OpenOffice Draw can read EPS files.  Try importing your EPS into that, then saving back out as a SVG.

---

### Post by gurlyburlyman on 2007-05-08
This response is probably too late for you to care, but the inkscape website suggests using gsview to convert pdf files to svg:

[http://wiki.inkscape.org/wiki/index.php/Current_PDF_Support#Use_of_Gnulibplot](http://wiki.inkscape.org/wiki/index.php/Current_PDF_Support#Use_of_Gnulibplot)

Unfortunately, gsview is not in the Ubuntu repositories, but you can download it easily enough (just do a quick google search).

---

### Post by hreker on 2007-07-14
I've had good results using (a demo version of) the [PDF2SVG]("http://www.pdftron.com/downloads.html") utility by a company called PDFTron.

---

### Post by furyy on 2008-04-01
SVG to PDF
```

git-clone git://cgit.freedesktop.org/~cworth/svg2pdf
cd svg2pdf
make
./svg2pdf in.svg out.pdf

```

and join multiple PDFs to one

```

gs -dBATCH -dNOPAUSE -q -sDEVICE=pdfwrite -sOutputFile=finished.pdf file1.pdf file2.pdf file3.pdf

```

---

