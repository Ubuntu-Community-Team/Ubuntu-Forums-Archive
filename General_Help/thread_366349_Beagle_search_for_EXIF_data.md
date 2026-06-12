---
title: "Beagle search for EXIF data?"
date: 2007-02-20
forum: General Help
---

### Post by TgBoat on 2007-02-20
I am trying to locate pictures I have taken by the camera I used.  I have beagle installed, but can't seem to get it to work.  Here are my results:

beagle-query --verbose dc210
Elapsed time: 1.633s
Total hits: 0


beagle-query --verbose dcp00780
First hit returned in 1.777s
Returned latest 1 results out of total 1 matches
  Uri: file:///array/media/AllPics/Pictures/Digital Pics/Random/dcp00780.jpg
PaUri: (null)
 Snip: (null)
 Type: File
MimeT: image/jpeg
  Src: Files
Score: 0
 Time: 2005-03-19 12:11:40 -05:00
    beagle:ExactFilename = 'dcp00780.jpg'
    beagle:Filename = 'dcp00780'
    beagle:FilenameExtension = '.jpg'
    beagle:HitType = 'File'
    beagle:InternalUri = 'uid:RCS108EW40CdgCK4aEqyUw'
    beagle:IsChild = 'false'
    beagle:MimeType = 'image/jpeg'
    beagle:NoPunctFilename = 'dcp00780'
    beagle:Source = 'Files'
    beagle:SplitFilename = 'dcp 00780'
    exif:ApertureValue = 'f/4.0'
    exif:Copyright = '[None] (Photographer) - [None] (Editor)'
    exif:ExposureTime = '1/30 sec.'
    exif:Flash = 'Flash fired.'
    exif:FNumber = 'f/4.0'
    exif:FocalLength = '4.4 mm'
    exif:Model = 'DC210 Zoom (V05.00)'
    exif:ShutterSpeedValue = '50/10 sec. (APEX: 5)'

Elapsed time: 1.958s
Total hits: 1


The model number is clearly listed.  Any idea why my initial search didn't catch it?

Thanks,
Bill

---

### Post by subdee on 2007-02-25
capitalisation, i presume...

> **TgBoat said:**
> I am trying to locate pictures I have taken by the camera I used.  I have beagle installed, but can't seem to get it to work.  Here are my results:

**dc210**
exif:Model = '**DC210** Zoom (V05.00)'

Any idea why my initial search didn't catch it?

Thanks,
Bill

---

