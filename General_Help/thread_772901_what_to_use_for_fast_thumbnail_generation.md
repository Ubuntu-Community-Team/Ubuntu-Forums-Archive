---
title: "what to use for fast thumbnail generation?"
date: 2008-04-28
forum: General Help
---

### Post by navidad on 2008-04-28
Hey there,
So I have folders and folders of huge TIFF picture files (200+ MB each). Is there a file manager and/or application that allows the quick generation of thumbnails for these TIFF images?? 

I'd rather not sit for 10 minutes trying to figure out what pictures are in the folder.

Thanks!

---

### Post by Patsoe on 2008-04-28
I would say, use find in combination with imagemagick's convert.
[http://www.imagemagick.org/script/command-line-processing.php](http://www.imagemagick.org/script/command-line-processing.php)

edit: more relevant link [http://www.imagemagick.org/Usage/thumbnails/](http://www.imagemagick.org/Usage/thumbnails/)

---

### Post by navidad on 2008-04-28
Ok, I get what you're saying about having a separate "Thumbnail" folder, and that's definitely doable (that method had slipped my mind). Though, I'd have to rerun thumb generation every time I changed the photo, maybe I can get that to run automatically, who knows.

I was rather referring to automatic thumbnail generation inside the file manager, like what thunar does (see attached) or even Windows explorer with its "preview" pane. Is there some application like that able to handle large files with ease?

---

### Post by Patsoe on 2008-04-28
I'm afraid I wouldn't know. You could try by copying three or four of your images into a test directory, and see how Nautilus (the standard file manager in Gnome that is) performs with such large files (I'm not sure it generates thumbnails for TIFFs at all though). You might also consider using F-Spot as a file browser (also part of the default apps).

Actually, doesn't the TIFF specification allow thumbnails to be embedded? I vaguely remember such an option when saving files as TIFF.

---

### Post by navidad on 2008-04-28
I'll definitely look into those. Thanks Patsoe!

---

### Post by TurboRush on 2008-04-28
You can try thumbnail.pl. Not sure how speedy it is for files of that size but I use it + a small java app to recurse directories and resize images for my website...

[http://www.lisbonne.com/digitalphotography.html]("http://www.lisbonne.com/digitalphotography.html")

---

