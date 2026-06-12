---
title: "Ideas for Renaming Multiple pdf Files?"
date: 2007-07-08
forum: General Help
---

### Post by kweejibo on 2007-07-08
I scanned 277 pages of an old automotive repair manual with Vuescan. By default, they are labeled yyyymmddhhmmss.pdf . I'd like to put the original page number on each one, but I haven't figured out an elegant way to view & change the name of the file. The file names will be <section>-<page> format (eg. 35-10), so I sort of need to be able to view the page number on the pdf file to do it. 

I tried blowing up the icon size to 400%, but the resolution is crappy in the icons and I can't read the numbers. Xpdf, Adobe Reader, and Evince do fine at opening an individual file, but there's no quick and dirty way to view the files and rename them!

Josh

---

### Post by jyba on 2007-07-08
There's a little utility called pstotext...
```
sudo apt-get install pstotext
```
...which can extract the text from pdf's. So if the page number is in a predictable place on each of your pages, or is in a predictable format (such as "Page 34" or "Section 12") you could write a simple script that uses sed or grep -o to extract that information and use it to build a new file name for each pdf.

---

### Post by aysiu on 2007-07-08
If the files are in order and there is a standard number of pages per section, you can use a batch-renaming application like KRename to save yourself some time.

---

### Post by kweejibo on 2007-07-09
jyba-

thanks for the pstotext idea. Somehow the page numbers (in the upper left corner of each page) don't seem to be decipherable by pstotext. Not sure why. I checked out <man pstotext> and couldn't find anything there that helped.

Josh

---

### Post by kweejibo on 2007-07-09
aysiu-

yes, scanning them in order would've been the clever route, but I didn't do that of course! i scanned the even side of the stack and then flipped it over and scanned the other, so it's a bit of a mish-mosh at this point.

Thanks,
Josh

---

### Post by tregeagle on 2007-07-11
I just had a similar mass file renaming problem and fixed it using Purrr (find it in the repo's)

sudo apt-get install purrr
and here is the howto/tutorial to go with it...
[http://mathrick.org/software/purrr.html](http://mathrick.org/software/purrr.html)

---

