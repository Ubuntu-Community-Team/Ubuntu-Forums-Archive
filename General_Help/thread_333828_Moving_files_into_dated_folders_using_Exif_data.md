---
title: "Moving files into dated folders using Exif data"
date: 2007-01-08
forum: General Help
---

### Post by Kabatwa on 2007-01-08
Hello all,

Recently I've not been able to find photos imported using the default import photos dialog as I now have quite a few photos and folders. The photos get put into folders dated with the date that I uploaded them to the computer. I've been wondering whether there is any way to rearrange these image files into folders using their creation date. For instance a file created on the 4th May 2006 would be put into a folder named 04-05-06.
I'm imagining there is some really simple way to do this using command line. I've looked at the command find with the option -ctime but still can't figure it out.
Also if there's a way to do this using a shell script that would be great because I'm just starting to learn shell scripts.

Thanks a lot

Tim

---

### Post by gumbald on 2007-04-20
This is something I'm looking to do to avoid having a 28 page album, instead I want day-by-day subalbums, can anybody suggest a way to sort by EXIF date or such? :)

---

### Post by fanatik on 2007-04-20
Well I don't think you will be able to get the create time of the file from the filesystem, ie using find or ls etc since its create time will be the date you uploaded them to the computer. you can install the exif package from universe:

```
$ sudo aptitude install exif
```

then you can use the data it provides to make your script:

```
$ exif imgp0012.jpg
```

will dump all the exif data out, which you can manipulate as you see fit.

```
EXIF tags in 'imgp0012.jpg' ('Motorola' byte order):
--------------------+----------------------------------------------------------
Tag                 |Value
--------------------+----------------------------------------------------------
Manufacturer        |PENTAX Corporation
Model               |PENTAX Optio S5i
Orientation         |top - left
x-Resolution        |72.00
y-Resolution        |72.00
Resolution Unit     |Inch
Software            |Optio S5i Ver 1.00
Date and Time       |2004:12:23 13:54:07
YCbCr Positioning   |centred
Unknown             |
Compression         |JPEG compression
x-Resolution        |72.00
y-Resolution        |72.00
Resolution Unit     |Inch
Exposure Time       |1/60 sec.
FNumber             |f/4.8
ISO Speed Ratings   |200
Exif Version        |Exif Version 2.2
Date and Time (origi|2004:12:23 13:54:07
Date and Time (digit|2004:12:23 13:54:07
ComponentsConfigurat|Y Cb Cr -
Compressed Bits per |5.50
Exposure Bias       |0.0
MaxApertureValue    |2.80
Metering Mode       |Pattern
Flash               |Flash fired, auto mode.
Focal Length        |17.4 mm
Maker Note          |27660 bytes unknown data
FlashPixVersion     |FlashPix Version 1.0
Colour Space        |sRGB
PixelXDimension     |2560
PixelYDimension     |1920
Custom Rendered     |Normal process
Exposure Mode       |Auto exposure
White Balance       |Auto white balance
Digital Zoom Ratio  |0/0
Focal Length In 35mm|105
Scene Capture Type  |Standard
Contrast            |Normal
Saturation          |Normal
Sharpness           |Normal
Subject Distance Ran|Close view
InteroperabilityInde|R98
InteroperabilityVers|
--------------------+----------------------------------------------------------
EXIF data contains a thumbnail (7216 bytes).

```

eg:
```
for img in img*.jpg
do
  DTE=$(exif "$img" | grep Date | head -n1 | cut -f2 -d'|' | cut -f1 -d' ' | tr ':' -)
  echo mkdir -p "$DTE"
  echo mv "$img" "$DTE"
done
```

I note there are 3 date fields in the exif data, I just chose the 1st one as an example.

Remove the echo commands to run the actual commands!

Regards,
James.

---

