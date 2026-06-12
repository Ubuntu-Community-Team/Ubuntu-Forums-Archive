---
title: "Resize images batch?"
date: 2005-07-01
forum: General Help
---

### Post by IchBin on 2005-07-01
Does anyone know of a way to resize all the images in a certain folder all at once? I have a bunch of logos that I'd like to make into avatar size about 90 x 90 pixels. I'm looking to make short work of this if possible.

---

### Post by Lunde on 2005-07-01
[QUOTE=IchBin]Does anyone know of a way to resize all the images in a certain folder all at once? I have a bunch of logos that I'd like to make into avatar size about 90 x 90 pixels. I'm looking to make short work of this if possible.[/QUOTE]
 Here's a howto for Imagemagic, you should look through the other stuff to on this page too.

[http://ubuntuguide.org/#bbips](http://ubuntuguide.org/#bbips)

---

### Post by ssam on 2005-07-01
something like

```
mogrify -quality 90 -geometry 90x90 file.jpeg
``` 

i think it overwrites the original file, so make sure you work on copies of the files

to get all the .jpeg files in the folder use

```
mogrify -quality 90 -geometry 90x90 *.jpeg
```

---

### Post by IchBin on 2005-07-01
Thanks guys I'll give this a shot over the weekend.

---

### Post by IchBin on 2005-07-05
That program worked fantastically. Only thing I have left to do is find a way to edit all the comments on my pictures. I noticed that this program only did that on jpg files. Is it possible to do this on png files in a similar batch process?

---

