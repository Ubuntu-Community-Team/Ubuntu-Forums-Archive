---
title: "Having trouble with large image file"
date: 2013-05-14
forum: General Help
---

### Post by Nixarter on 2013-05-14
OK, so I took this big (ok, huge) panorama on a beach where I live and stitched it with hugin.  For some reason the linux version of hugin scales down images before it works on them by like 40%, but it still ended up being 114 megapixels and ~450mb (tiff file).  Image viewer wont open it.  Shotwell wont open it all, but it will let me zoom in and I can see all of it (scroll around).  Apparently it only opens what I'm looking at at one given time.  So the image exists and it all looks good (takes forever to scroll around. 50k pixels wide... ~40 screen widths lol, but i checked it all :) ).  I hit save as and picked jpeg... and it tries for a bit... then crashes out.

Is there any way to convert this big tiff file into a more RAM-friendly jpeg version (perhaps through terminal)?  Or, maybe to resize the tiff so that I can actually open the thing?

Any other ideas on what I can do?  I'd still like to adjust sharpness, contrast, color, etc.  But apparently I have to get it to a smaller size for gimp or PS to hande it.  :(  And I'd also like to share it... but ~450mb is waaay to big for that.

---

### Post by Nixarter on 2013-05-14
Well, apparently before it crashed it actually did save a jpeg image correctly.  Compressed down to 25.7mb!  I still can't open it in an image editing program, though.  I have to fix soem crop artifacts (make some ocean to fill in a bit of black lol).

---

### Post by SeijiSensei on 2013-05-14
You should become familiar with the command-line tools in the [Imagemagick]("http://www.imagemagick.org/") kit.  You can apply a wide variety of image transforms at the command prompt including scaling and format conversion.  Use "sudo apt-get install imagemagick" to install a copy.

---

