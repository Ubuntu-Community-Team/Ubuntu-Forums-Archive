---
title: "how to write/append TIFF file in ubuntu 14.04"
date: 2017-07-06
forum: General Help
---

### Post by bhaaskarr on 2017-07-06
Hi,

I am using Ubuntu 14.04.
SXIV (simple X Image Viewer) is used to view TIFF image file where it uses "Imlib2" Image library for loading TIFF files.
it uses below lines
 file = fopen(im->real_file, "rb");
 tif = TIFFFdOpen(fd, im->real_file, "r");
//[http://muennich.github.io/sxiv/sxiv.1.html](http://muennich.github.io/sxiv/sxiv.1.html)//

I would like to know how to write/append data in TIFF file? like using below statements
 tif = TIFFFdOpen(fd, im->real_file, "w");
 tif = TIFFOpen(fd, im->real_file, "w"); //write/append mode.

Your help is much appreciated.

---

