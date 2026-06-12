---
title: "Edit/View XMP Google Photosphere"
date: 2016-08-04
forum: General Help
---

### Post by theonlytalkinggoat on 2016-08-04
I am looking for a way to view and edit the xmp data or tags that are embedded into photosphere images, for Google. In order to build photospheres, the xmp data must be added in. I tried using Digikam, but the version int he repos, 4.14, doesn't seem to read the xmp data and I'm not sure if exiv2 is reading it correctly, or, how to read it, for that matter. Does anyone know of a program that will easily add or edit the xmp data?

---

### Post by col48 on 2016-08-04
An internet search turned up this, but I think you may have already looked.  It doesn't look very hopeful, I'm afraid.

[http://libre-software.net/edit-image-metadata-on-linux/]("http://libre-software.net/edit-image-metadata-on-linux/")

---

### Post by theonlytalkinggoat on 2016-08-04
I had seen XnViewMP and it looks promising, but it can't edit the data. Gimp strips out the XMP data, completely, so if you need to edit an image, you better have a backup of your XMP, to re-import, or Gimp will destroy it. The command to read the XMP data in exiv2 is as follows:
```

exiv2 -px pr [filename].JPG

Xmp.GPano.ProjectionType                     XmpText    15  equirectangular
Xmp.GPano.UsePanoramaViewer                  XmpText     4  True
Xmp.GPano.CroppedAreaImageWidthPixels        XmpText     4  5376
Xmp.GPano.CroppedAreaImageHeightPixels       XmpText     4  2688
Xmp.GPano.FullPanoWidthPixels                XmpText     4  5376
Xmp.GPano.FullPanoHeightPixels               XmpText     4  2688
Xmp.GPano.CroppedAreaLeftPixels              XmpText     1  0
Xmp.GPano.CroppedAreaTopPixels               XmpText     1  0
Xmp.GPano.PoseHeadingDegrees                 XmpText     5  180.0
Xmp.GPano.PosePitchDegrees                   XmpText     3  9.1
Xmp.GPano.PoseRollDegrees                    XmpText     4  -2.5

```

I'll get back to you, on how to export, edit and re-attach.

---

