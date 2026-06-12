---
title: "Add a timestamp to photos by reading the file date...?"
date: 2007-09-11
forum: General Help
---

### Post by FSHero on 2007-09-11
I'm working with my photo's, and none of them have a timestamp on the picture automatically added by the camera. (Good when using as desktop backgrounds; bad when printing!)

Is there a program that can add a timestamp to an image by reading the EXIF info, or the file creation date? Preferably native for GNU/Linux, preferably free/open-source.

I did a quick google search on "timestamp images", and it led me to TimeToPhoto: [http://avpsoft.com/products/timetophoto/?g=timetophoto.com](http://avpsoft.com/products/timetophoto/?g=timetophoto.com)
Something like that would be nice. It seems to add the date to the corner of the picture.

Thanks all,
FSHero :-)

---

### Post by mrxinu on 2007-09-11
I don't know how close to the metal you want to get, but the ImageMagick package does this really well once you get the command-line sorted the way you want it.

[http://www.imagemagick.org/Usage/annotating/#wmark_text](http://www.imagemagick.org/Usage/annotating/#wmark_text)

You can read EXIF data with 'exiv2'.

---

### Post by mal on 2007-09-11
Try jhead.

$ sudo apt-get install jhead
$ man jhead

I think it has an option to do exactly what you are after.

Regards,

Mal

---

### Post by FSHero on 2007-09-12
Thanks guys,

Actually, I don't want to edit the EXIF data, but the actual image pixels themselves.

I'll look at that ImageMagick later. I asked this same question on [www.linuxquestions.org](www.linuxquestions.org) and someone mentioned something similar.

I'll report back when I use ImageMagick.

---

