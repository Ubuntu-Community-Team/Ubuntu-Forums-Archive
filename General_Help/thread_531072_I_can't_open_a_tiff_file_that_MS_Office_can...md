---
title: "I can't open a tiff file that MS Office can.."
date: 2007-08-21
forum: General Help
---

### Post by senectus on 2007-08-21
I have a .tiff file that was generated from a Fuji Xerox scanner (DC450), for some reason I can't open it  from Ubuntu but in WinXP I can.
Is there some app that will convert (even command line) a tiff to .jpg for me?

---

### Post by kellemes on 2007-08-21
You want to convert it?
A tif is a raw image file you can open with packages that deal with stuff like that.
Like [f-spot]("http://f-spot.org/Main_Page")

---

### Post by mcduck on 2007-08-21
> **kellemes said:**
> You want to convert it?
A tif is a raw image file you can open with packages that deal with stuff like that.
Like [f-spot]("http://f-spot.org/Main_Page")

No, Tiff is not a raw image file. It just allows saving files without compression but it's still just a normal image format. And any decent photo editor should open basic tiff files, in Ubuntu try Gimp.

If it still refuses to open the problem may be that tiff can store more than just a single image, it's actually freely extensible format and if the file has some uncommon stuff in it it might be impossible to open with any other program than the one used to create it in the first place.

[http://en.wikipedia.org/wiki/Tagged_Image_File_Format]("http://en.wikipedia.org/wiki/Tagged_Image_File_Format")

---

### Post by manimal on 2007-08-21
Install "imagemagick."   This package contains the command-line program "convert."   As the name suggests, "convert" will convert an image to a different file type.  Example:

convert image.tiff image.jpg

Convert will do lots of other things too.  Check out the "man" page.

---

### Post by kellemes on 2007-08-21
> **mcduck said:**
> No, Tiff is not a raw image file. It just allows saving files without compression but it's still just a normal image format. 

I stand corrected.

---

