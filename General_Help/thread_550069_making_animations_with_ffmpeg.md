---
title: "making animations with ffmpeg"
date: 2007-09-13
forum: General Help
---

### Post by Joe Momma on 2007-09-13
I need some help animating a series of images into an mpeg.  I've tried searching the forums but couldn't find a solution.

I have a collection of image files (tif format) and I am trying to combine them into an mpeg.

The files are named 000100.tif, 000200.tif, ... 050000.tif

when I run:
        ffmpeg -i 0%3d00.tif a.mpg

I get the following error:

        0%3d00.tif: I/O error occured
        Usually that means that input file is truncated and/or corrupted.

I'm pretty sure the images are not corrumpted

Then I tried converting them all to jpg with the "convert" command and running:
        ffmpeg -i 0%3d00.jpg a.mpg

this produces an output mpg file, but it is not playable in either totem or windows media player.


Does anyone think they can help?

---

