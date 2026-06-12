---
title: "Still no good solution for simple VCD/DVD authoring in Gutsy?"
date: 2008-03-22
forum: General Help
---

### Post by sarc on 2008-03-22
Devede asks for impossibly high file sized - wants 100GB free space to make a 2GB DVD.  If I try to use my FAT32 partition it complains that it does not like FAT

Todisc crashes trying to make a DVD.

Tried DVDstyler in Windows but could not install in Gutsy even with the very helpful howtos - lots of dependency issues

Surely there is a way to make a VCD and DVD from ogg files (ripped from Thoggen)  that is simple and works every time?

Thanks

---

### Post by cotcot on 2008-03-22
Have you checked qdvdautjor ?

---

### Post by sarc on 2008-03-22
I tried it and showed an 'ERROR!" message for the ogg files.  OK I think Thoggen has got to go.  Bacl to DVD:rip!

---

### Post by cotcot on 2008-03-25
Have you checked the paths in Qdvdauthor ? See Tools --> Setup --> Paths. Try the Scan System button to inform the program where to find decoders etc. If there remain red colored fields then you have to install the missing package. Under the Man button you can find which one. For instance Vorbis Tools for ogg. Good Luck.

---

### Post by danwood76 on 2008-03-25
You could always use Avidemux2 to convert the ogg to mpeg2 files which is the DVD format.
This will save your DVD authoring program from having to transcode the video.

I make DVDs with qdvdauthor all the time and never have any issues if I convert the videos first.

---

### Post by sarc on 2008-03-25
Dang Thoggen is slow enough as is (11 frames/second) ripping my CDs, and Devede transcoded the ogg to mpg and there was a big loss in picture quality - worried about the same thing if I transcode myself.  This is just so painful...

---

### Post by danwood76 on 2008-03-26
transcoding in avidemux2 is easy and excellent picture quality.
It has auto settings so you can just click DVD and it will auto set it up.

Get the 2.4 version from getdeb.com.
There are quite a few quides to preparing dvds in qdvdauthor (you can also get version 1 of qdvdauthor from getdeb)

The atart of this guide is for avidemux2
[http://avidemux.org/admForum/viewtopic.php?id=3570](http://avidemux.org/admForum/viewtopic.php?id=3570)

Heres the guide from the qdvdauthor site on creating a DVD
[http://qdvdauthor.sourceforge.net/guide/f_complex.html](http://qdvdauthor.sourceforge.net/guide/f_complex.html)

---

### Post by sarc on 2008-03-26
Will try out asap, thanks...

---

