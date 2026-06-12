---
title: "Problem running ImageMagick 7 on Ubuntu 20.04"
date: 2022-06-07
forum: General Help
---

### Post by satimis on 2022-06-07
Hi all,

I need to install ImageMagick verions 7 and followed below document to install it from source.

How to install ImageMagick 7 on Ubuntu
[https://scottiestech.info/2020/05/26/how-to-install-imagemagick-7-on-ubuntu/comment-page-1/](https://scottiestech.info/2020/05/26/how-to-install-imagemagick-7-on-ubuntu/comment-page-1/)

Installation went through without difficulty and complaint.  Now I have ImageMagick 7.1.0-37 running.

$ identify -version```

Version: ImageMagick 7.1.0-37 Q16-HDRI x86_64 20104 https://imagemagick.org
Copyright: (C) 1999 ImageMagick Studio LLC
License: https://imagemagick.org/script/license.php
Features: Cipher DPC HDRI Modules OpenMP(4.5) 
Delegates (built-in): fontconfig freetype jp2 ltdl png webp x zlib
Compiler: gcc (9.4)

```

But I could not run their command;

~/Desktop$ convert -rotate 90 20220606_a1.jpg 20220606_a1_90.jpg ```

convert: no decode delegate for this image format `JPG' @ error/constitute.c/ReadImage/738.
convert: no images defined `20220606_a1_90.jpg' @ error/convert.c/ConvertImageCommand/3325.

```

~/Desktop$ ls```

20220606_a1.jpg  p_01_20220523.jpeg  PC1_20220604  PC1a_20220604

```

The image file is there.

Please help.  Thanks

Regards

---

### Post by Holger_Gehrke on 2022-06-07
The third comment on the page you linked to has (one) solution. Basically ImageMagick relies on 'delegates' for image coding and decoding and the default configuration doesn't have some of the most common formats included (no jpeg, no tiff, ...). By using the ImageMagick Easy Install script linked in that comment, you save yourself the trouble of looking up the various options to 'configure' and finding / installing the headers for the various libraries which you need to get full support for all the formats you will need.

Holger

---

### Post by satimis on 2022-06-07
> **Holger_Gehrke said:**
> The third comment on the page you linked to has (one) solution. Basically ImageMagick relies on 'delegates' for image coding and decoding and the default configuration doesn't have some of the most common formats included (no jpeg, no tiff, ...). 

Yes

I have tried it before, following Step-2 of my linked article.

Step 2: Just in case, install all the build dependencies for ImageMagick:

$ sudo apt build-dep imagemagick```

Reading package lists... Done
E: You must put some 'deb-src' URIs in your sources.list

```
I couldn't figure it out and skipped it.

> 
By using the ImageMagick Easy Install script linked in that comment, you save yourself the trouble of looking up the various options to 'configure' and finding / installing the headers for the various libraries which you need to get full support for all the formats you will need.

I need ImageMagick7.

-white-balance
doesn't work on ImageMagick6.

The script is for installing ImageMagick6

Regards

---

