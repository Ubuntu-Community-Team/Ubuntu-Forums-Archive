---
title: "convert image format of very large image"
date: 2020-04-21
forum: General Help
---

### Post by Skaperen on 2020-04-21
i have a very large image in .pnm format.  i want to convert it to .jpg format.  the *convert* command tells me it exceeds the limit.  the size is 1920x63523.  any other way to convert it?  is the limit 65535 or 32767?

---

### Post by ActionParsnip on 2020-04-22
Does EOG do it?

---

### Post by mIk3_08 on 2020-04-22
Try using GIMP. I think gimp can convert large format images.

---

### Post by ActionParsnip on 2020-04-22
[https://www.imagemagick.org/discourse-server/viewtopic.php?t=34044](https://www.imagemagick.org/discourse-server/viewtopic.php?t=34044)

Seems the "-limit memory" option can be used. Just specify a high amount of RAM like 8192Mb (I assume you have more than 8Gb RAM). You get the idea

---

### Post by mIk3_08 on 2020-04-22
[ImageMagick]("https://www.imagemagick.org/discourse-server/viewtopic.php?t=34044") 
>  Seems the "-limit memory" option can be used. Just specify a high amount of RAM like 8192Mb (I assume you have more than 8Gb RAM). You get the idea 
Another option is to use ```
gdalwarp
``` part of GDAL. and ImageMagick will do for more than 5GB image I think.

---

