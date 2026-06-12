---
title: "Command merging 2 images"
date: 2017-04-13
forum: General Help
---

### Post by satimis on 2017-04-13
Hi all,

Instead of running GIMP is there command to merge 2 images?

example:
image-1.png  Text with transparent background
image-2.png  For background

Thanks

Regards
satimis

---

### Post by ajgreeny on 2017-04-13
I am sure you could do that with imagemagick, so have a good long look through their own (huge) page at [http://imagemagick.org/Usage/layers/#append](http://imagemagick.org/Usage/layers/#append) where hopefully you may find an example of more or less what you want.

I have used imagemagick many times in the past and even have an image-resize custom action set in my Xubuntu thunar right click context menu, but I admit I have never used it to do something like you want.

---

### Post by satimis on 2017-04-13
> **ajgreeny said:**
> I am sure you could do that with imagemagick, so have a good long look through their own (huge) page at [http://imagemagick.org/Usage/layers/#append](http://imagemagick.org/Usage/layers/#append) where hopefully you may find an example of more or less what you want.

I have used imagemagick many times in the past and even have an image-resize custom action set in my Xubuntu thunar right click context menu, but I admit I have never used it to do something like you want.
Hi,

Thanks for your link.

Following command works for me seamlessly;```

&#10219; composite -blend 80 -gravity center chinese_08_transp.png scenery-008.jpg output_file.png

```

Regards
satimis

---

### Post by ajgreeny on 2017-04-14
Brilliant!

Thanks for marking as solved.

---

