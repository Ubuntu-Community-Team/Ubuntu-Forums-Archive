---
title: "ps to djvu"
date: 2008-07-05
forum: General Help
---

### Post by orlox on 2008-07-05
Hi!

Is there a way to transform big ps files to djvu??

---

### Post by ryanhaigh on 2008-07-06
[http://any2djvu.djvuzone.org/](http://any2djvu.djvuzone.org/)

You might also check out imagemagick, I can't try it as Im not on an ubuntu machine at the moment but it may be as simple as 
```
convert file.ps file.djvu
```

---

### Post by tonytraductor on 2011-05-21
I've been trying to do this, in fact, plain text to djvu, but without using pdf as an intermediary.

Now, imagemagick convert does not write djvu.
Try, and you get
convert: no encode delegate for this image format `file.djvu' @ error/constitute.c/WriteImage/1153.

I have a script that converts plain text to djvu (but uses ps2pdf then pdftodjvu to do it) here: 
[http://baldwinsoftware.com/blog/2011/01/19/convert-plain-text-to-djvu/](http://baldwinsoftware.com/blog/2011/01/19/convert-plain-text-to-djvu/)

I'm trying, NOW, to do it without pdf.

I've been trying to use pstopnm and then either c44 or cbj2 to convert the resultant pnm image to djvu, but I keep getting blank/empty files.
There's discussion of the matter in the comments to the above linked blog entry.

I'd be interest in any feedback on that, and/or news of anybody successfully doing this, either txt to djvu without pdf in there, or, of course, even just ps to djvu, without pdf as mediary.

---

