---
title: "Rename Many Files"
date: 2007-06-09
forum: General Help
---

### Post by an.echte.trilingue on 2007-06-09
I am using a tool called pngnq to shrink many hundreds of .png pictures that I intend to put on a website.  The problem is, all of the output files are called filename-nq8.png and I would like to keep filename.png as the filename; pngnq has an option that is supposed to do this automatically but it looks broken.  Is there any way to rename all of these files without doing each one by hand?

Thank you, 

-mat

---

### Post by Darling on 2007-06-09
sudo aptitude install thunar

Thunar is the Xfce (Xubuntu) file manager. And that also contains a tool ThunarBulkRename. That might help you.
However, why don't you use ImageMagick convert or mogrify  to change the Png files?

---

### Post by an.echte.trilingue on 2007-06-09
> **Darling said:**
> sudo aptitude install thunar

Thunar is the Xfce (Xubuntu) file manager. And that also contains a tool ThunarBulkRename. That might help you.
However, why don't you use ImageMagick convert or mogrify  to change the Png files?

I would prefer a command line tool, if you know of one.  The machine where the files are located doesn't have X installed.  

As for the question, I should have been clearer.  I am not shrinking the size of the images, I am shrinking the size of the files.  I am making a series of rollover maps with high-contrast maps, so I can't live with the artifacts that JPG leaves.  Since many 10+ images must download for each map before it will display, size is critical.   Optimized GIFs for the images in question are about twice the size of optimized PNGs.  I want to use pngnq specifically because it gives me the best compression (a 400px by 300px map with an original file size of 34kb compresses to around 8kb, versus 24kb with optipng, 25 with GIF straight from the GIMP and 16kb with GIFs after I have played with them a bit) without sacrificing appearance like pngquant does.  

Thanks,
-mat

---

### Post by an.echte.trilingue on 2007-06-10
Found the solution:```
rename 's/-nq8.png/.png/' *.png
```Take care everybody.
-mat

---

