---
title: "Pdf"
date: 2012-12-22
forum: General Help
---

### Post by ushaanpathe on 2012-12-22
Hi,

1) Want to know how to reduce the PDF size

2) How to remove the true & false formula through Paste special

3) How to edit in the PDF 

  :-k

---

### Post by fdrake on 2012-12-22
> **ushaanpathe said:**
> Hi,

1) Want to know how to reduce the PDF size

2) How to remove the true & false formula through Paste special

3) How to edit in the PDF 

  :-k

1,2. don;t know
3. gimp image editor (you can edit page by page only) 

may I give you the advice of having a dulboot with win7/xp for your office routine just in case ubuntu doesn't fullfill all your needs... acrobat runs better in win...

---

### Post by sudodus on 2012-12-22
Welcome to the Ubuntu Forums :-)

When I used the previous Ubuntu long time support version, 10.04, I used Ghostscript to shrink pdf files.

Type

```
gs -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=setting -sOutputFile=output.pdf input.pdf
```into the Terminal window, replacing "input.pdf" with the name of your PDF file and "setting" with a desired quality level, and then press "Enter."

Quality level settings are "/screen," the lowest resolution and lowest file size, but fine for viewing on a screen; "/ebook," a mid-point in resolution and file size; "/printer" and "/prepress," high-quality settings used for printing PDFs.

In general I would discourage editing pdf files, because it is meant to be a final document format. But sometimes you want to make notes or fill in a form 'on top of' a pdf document. Then you can use ***xournal***. Install it from the repositories with

```
sudo apt-get install xournal
```

---

### Post by Impavidus on 2012-12-22
> **ushaanpathe said:**
> Hi,
1) Want to know how to reduce the PDF size
2) How to remove the true & false formula through Paste special
3) How to edit in the PDF 
  :-k
1: Pdf is a container that can contains (usually) static 2D graphics. These can be in raster format (a raster of pixels each having their own colour)  or in vector format (instructions like: "put an arc here with radius r, thickness t, colour x from 0 to 90 degrees). If the pdf contains graphics in raster format the file size can be reduced by reducing the resolution or increasing the (lossy) compression, which both leads to a reduction in quality. See post #3. If it is in vector format the file is usually not very large, so there's no reason to make it smaller, which would be complicated anyway. If you're creating the pdfs yourself there are some extra tricks available, but that's something of a black art that has to be performed on a case-by-case basis.

2: I don't know.

3: Don't edit pdfs if it can be avoided. Edit the source of the pdf instead. If you have to edit a pure raster pdf you can you use **gimp**, but if your pdf also contains vector graphics or (raster) text (or even different blocks of raster graphics at different resolutions) **inkscape** does a better job by not increasing file size (too much) and keeping the original resolution, without recompressing the raster graphics. That is because inkscape can save to vector format. If necessary, you can use inkscape to extract raster graphics from a pdf containing, for example, both photos and text, use gimp to edit the photos and use inkscape to reinsert the photos into the pdf. I never tried it though.

---

### Post by mike555 on 2012-12-22
You should be able to edit a pdf in LibreOffice if you have the pdf import ad-on.
     There are websites that will shrink pdfs for you, or you can get the ad-on " RIOT " ... for the GIMP .... [http://luci.criosweb.ro/riot/download/](http://luci.criosweb.ro/riot/download/)

---

