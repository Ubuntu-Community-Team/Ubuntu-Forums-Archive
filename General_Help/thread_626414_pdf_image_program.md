---
title: "pdf image program"
date: 2007-11-29
forum: General Help
---

### Post by spvo on 2007-11-29
Recently I've been having to scan a lot of documents, via a xerox machine, to convert them to pdf.  The machine scans a whole stack of stuff and just emails me a pdf that I can easily seperate using pdftk.  That works great.

However, a few of the pages I need to make minor edits to.  I used pdfimages to convert the needed page into an image, it saves it as a pbm file.  GIMP lets me easily edit that.  Then I convert the edited image back into a pdf using "convert".  And rejoin it into a document using pdfjoin. The problem is that the final pdf is always significantly larger than what I started with, and I can't figure out why.

When I saved the edited image as a pbm file the pdf was huge.  When I saved the edited image as a png file the pdf was still much larger than it was before.  What format should I save the edited image as?  Also, should I be using another program or method to do this?  Any help would be appreciated.

John

---

### Post by indytim on 2007-11-29
I'm not familiar with the app pdfimages.  If it helps, within GIMP, you can use the Image->Scale Image to re-scale your image down to, say 8.5x11.  That might address the growth situation you are experiencing before converting back to pdf.

IndyTim

---

### Post by vanadium on 2007-11-29
I suspect that somewhere in your conversion (probably the convert step), the bit depth is increased. Your original pdfs contain graphics with only black and white. Probably, your edit in gimp preserves that. I expect it is convert where the (undesired) conversion occurs. You could test that by extracting the image from the newly created PDF. Another possibility is that convert does not compress the PDF. In that case, you could try compressing the PDF with pdftk.

---

### Post by spvo on 2007-11-29
vanadium,

I just tried out what you suggested, and convert is where the problem occurs.  Taking the original pdf, pdfimages created a pbm file for each page.  Immediately recombining those into a pdf using convert ended in a pdf 10 times the size.  Then using pdfimages on that file resulted in a ppm file for each page.  The ppm file is much larger than the pbm file, I'm assuming its because its capable of more than just two colors.

Do you know of anything, other than convert, to create a pdf out of an image?

---

### Post by spvo on 2007-11-29
One more thing.  I did try recompressing the pdf after convert created it, and the file size didn't change.

---

### Post by vanadium on 2007-11-30
You narrowed down the problem. Unfortunately, I do not know right away how you could do the conversion to PDF, maintaining a bit depth of only 2 in the graphics. I guess it must be possible passing the appropriate options. Take a look at de convert options, or alternatively, try to directly run ghostscript (gs) for converting the image to pdf. It is something that I would like to know as well. I will also take a look and post back if I find something useful.

---

### Post by vanadium on 2007-11-30
I found the solution, though it took me a few hours. It works like this:

```

convert -density 300 -units PixelsPerInch ex-000.pbm ex.ps
ps2pdf13 -sPAPERSIZE=a4 ex.ps ex.pdf

```

An important point is to explicitly set the proper resolution of you material. This information seems not to be present in the pbm. This is done by -density 300 -units PixelsPerInch 

For a strange reason, I also had to -negate in the first command (invert colors): my pbm's (from a PDF xerox) came out in negative from pdfimages.

The critical point for obtaining (and retaining) the small file sizes is that the black/white graphics are compressed using Group4 compression. Only that compression gave me a tif file equal in size to the initial PDF. Curiously enough, I could not use convert to turn that in a small PDF: a 560 K file resulted, irrespective of the -compress setting, where ghostscript manages to reproduce the small 75 K file. Ghostscript seems to be using the Group4 compression by default.

For the gurus among us, both commands can be piped:

```

convert -negate -density 300 -units PixelsPerInch ex-000.pbm ps:- | ps2pdf13 -sPAPERSIZE=a4 - ex.pdf

```

If you want to edit the PDF, in the first command, specify tif as output extension. Then edit the tif, and convert it to postscript (ps) using a plain:

```

convert ex.tif ex.ps

```

before feeding the ps to ghostscript.

I found this after a few hours. If I leave you now, you will be knocking at this door again before the evening. Indeed, another issue will pop up also for you probably. If your PDF scanner works like ours, then the pbm will have no margins, which is optimal for minimal size. However, following my procedure, you will end up with a new PDF where the page ends up with no bottom and left margins.

It took me a few other hours to find a solution. I did not manage to find an option that would allow me to adjust the margins, i.e. control the placement of the PDF on the page. However, following approach  worked. It involves placing your page on a tif representing an empty page (a4 in my case) using composite. Thus, create an a4 in the gimp, giving it the proper resolution (i.e. that corresponding with your source material). Then center your 

```

composite -density 300 -units PixelsPerInch -compose  atop -gravity Center ex.tif a4.tif exa4.tif

```

You can also indicate the pbm directly on the command line. Convert now exa4.tif to a pdf. The size overhead in the final PDF of adding the "graphical" margins is close to nothing.

---

### Post by spvo on 2007-11-30
Wow, thanks for spending so much time to help me out with the problem.  I really do appreciate the effort you spent to help me with the problem.

I found a program called tiff2pdf, which is able to convert a tiff directly into a pdf without the insane amount of bloat.  So I just used Gimp to edit them, saved as a tiff (using the CCITT group 4 fax compression), and converted that back to a pdf.

Using this method kept the pdf about 1/3 the size of the other best method I had found (using convert and jpeg or png).  Also the smaller size files print significantly faster.

The margins I'm not really worried about.  They print fine, and as long as all the pages in a pdf have the same oversized margins I'm happy.

Thanks again,
John

---

### Post by vanadium on 2007-12-01
Well indeed, your solution is by far the most simple and convenient! I had found the utility tiff2pdf myself, but I guess that hours of searching is not good anymore for mental health and finding good solutions.

In short,

convert file.pbm file.tif
tiff2pdf -o file.pdf file.tif

works, but if you want to control page size of the pdf, you need to add the options to set the tiff resolution in the convert command, and the page size in the second command. A big thank back to you from my part.

---

### Post by jkzubu on 2007-12-01
edit

---

