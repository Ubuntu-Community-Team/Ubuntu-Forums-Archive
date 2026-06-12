---
title: "which Document Viewer shall I install?"
date: 2022-07-19
forum: General Help
---

### Post by satimis on 2022-07-19
Hi all,

Ubuntu 20.04 desktop

Reading an old .tif file on my database it popup following warning:```

This image contains multiple pages. Image Viewer displays only the first page.
You may want to install the Document Viewer to see all pages.

```
and showing an old photo

Please advise which Document Viewer shall I install?

Thanks.

Regards

---

### Post by Holger_Gehrke on 2022-07-19
That message talks about the standard 'Document Viewer' aka evince which - according to [https://wiki.gnome.org/Apps/Evince/SupportedDocumentFormats](https://wiki.gnome.org/Apps/Evince/SupportedDocumentFormats) will read multi-page tiff files using libtiff. On a standard Ubuntu install it should already be installed, but if it isn't then 'sudo apt install evince' will do the trick.

Holger

---

### Post by satimis on 2022-07-19
> **Holger_Gehrke said:**
> That message talks about the standard 'Document Viewer' aka evince which - according to [https://wiki.gnome.org/Apps/Evince/SupportedDocumentFormats](https://wiki.gnome.org/Apps/Evince/SupportedDocumentFormats) will read multi-page tiff files using libtiff. On a standard Ubuntu install it should already be installed, but if it isn't then 'sudo apt install evince' will do the trick.

Holger
Thanks for your advice.

"evince" is already installed and running here.

On Terminal:
$ which evince```

/usr/bin/evince

```

Again on Terminal:
$ evince ~path-to-folder/file01.tif

It starts a screen showing 2 pages there. But it is quite strange to me, clicking either page-1 or page-2 it shows the same photo.

Pls refer to attached screenshot.

Regards

---

### Post by Holger_Gehrke on 2022-07-19
Might be different resolutions of the same image. Try 'identify -verbose ~/path-to-folder/file01.tif'. This should give you a rather detailed description of what's in the file. You could also try to import it into gimp; the different pages should get loaded as separate layers.

Holger

---

### Post by satimis on 2022-07-19
> **Holger_Gehrke said:**
> Might be different resolutions of the same image. Try 'identify -verbose ~/path-to-folder/file01.tif'. This should give you a rather detailed description of what's in the file. You could also try to import it into gimp; the different pages should get loaded as separate layers.

Holger

Before posting I have tried starting the file with GIMP

Right click "file01.tif" -> Open With Other Application

Select -> GNU Image Manipulation Program

Import from TIFF -> OK -> Import

GIMP Message```

TIFF image Message
file-tiff: Null count for "Tag 34391" (type 1,writecount-3, passcount 1)
OK

```
-> OK

only ONE image found

$ identify -verbose anne+rey\ 007.tif | more
```

Image: anne+rey 007.tif
  Format: TIFF (Tagged Image File Format)
  Mime type: image/tiff
  Class: DirectClass
  Geometry: 1027x1299+0+0
  Resolution: 299.999x299.999
  Print size: 3.42334x4.33001
  Units: PixelsPerInch
  Colorspace: sRGB
  Type: TrueColor
  Endianess: LSB
  Depth: 8-bit
  Channel depth:
    red: 8-bit
    green: 8-bit
    blue: 8-bit
  Channel statistics:
    Pixels: 1334073
    Red:
      min: 0  (0)
      max: 255 (1)
      mean: 176.296 (0.691358)
      standard deviation: 61.8479 (0.242541)
      kurtosis: -0.870442
      skewness: -0.792591
      entropy: 0.910588
    Green:
--More--identify-im6.q16: Unknown field with tag 34391 (0x8657) encountered. `TIFFReadDirectory' @ warning/tiff.c/TIFFWarnings/949.
identify-im6.q16: Unknown field with tag 34392 (0x8658) encountered. `TIFFReadDirectory' @ warning/tiff.c/TIFFWarnings/949.
identify-im6.q16: anne+rey 007.tif: Null count for "Tag 34391" (type 1, writecount -3, passcount 1). `_TIFFVSetField' @ error/tiff.c/TIFFErrors/604.
identify-im6.q16: Unknown field with tag 317 (0x13d) encountered. `TIFFReadDirectory' @ warning/tiff.c/TIFFWarnings/949.
....
....
....

```

It is a large file.

Regards

---

### Post by Holger_Gehrke on 2022-07-19
According to the [TIFF-Tag reference]("https://www.awaresystems.be/imaging/tiff/tifftags/extension.html") I found online, tag 317 is an extension tag for storing a predictor (a mathematical operator applied to an image before compression is applied). The other one - tag 34391 - is in a numerical range where private tags are found and the closest to this number is one used by Adobe Photoshop, but the list of private tags in that reference is limited to the ones which were at some point in time documented by the people who defined and used them. This file was probably created with some proprietary app (Photoshop, possibly) and uses some additional tags for blocks of data that aren't generally assumed to be of use outside of the application that wrote the file. Unless this file is from the 'wild west' days of image storage (late 80's to early 90's) the image blocks are probably all readable but there might be some secondary stuff (color balance or gamma factors for example) stored in there in a way that can't be recovered by anything but the program that wrote the file. Since you (sensibly, identify just loves to spew out detailed data if you allow it to be verbose) left out quite a lot of the data, it might be uncompressed which would explain the file size ... TIFF can contain images in all kinds of encodings (that's what the tags are for, among other things - to declare the compression method used on a block of image data) but uncompressed TIFF used to be a common way to store images which one either expected to store for the long term or which was going to be used in some kind of ongoing work.

Holger

---

### Post by satimis on 2022-07-20
> **Holger_Gehrke said:**
> According to the [TIFF-Tag reference]("https://www.awaresystems.be/imaging/tiff/tifftags/extension.html") I found online, tag 317 is an extension tag for storing a predictor (a mathematical operator applied to an image before compression is applied). The other one - tag 34391 - is in a numerical range where private tags are found and the closest to this number is one used by Adobe Photoshop, but the list of private tags in that reference is limited to the ones which were at some point in time documented by the people who defined and used them. This file was probably created with some proprietary app (Photoshop, possibly) and uses some additional tags for blocks of data that aren't generally assumed to be of use outside of the application that wrote the file. Unless this file is from the 'wild west' days of image storage (late 80's to early 90's) the image blocks are probably all readable but there might be some secondary stuff (color balance or gamma factors for example) stored in there in a way that can't be recovered by anything but the program that wrote the file. Since you (sensibly, identify just loves to spew out detailed data if you allow it to be verbose) left out quite a lot of the data, it might be uncompressed which would explain the file size ... TIFF can contain images in all kinds of encodings (that's what the tags are for, among other things - to declare the compression method used on a block of image data) but uncompressed TIFF used to be a common way to store images which one either expected to store for the long term or which was going to be used in some kind of ongoing work.

Holger
Your advice noted.  Thanks

Regards

---

