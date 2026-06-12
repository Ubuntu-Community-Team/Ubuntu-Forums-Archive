---
title: "Blender to Kino"
date: 2005-05-18
forum: General Help
---

### Post by credo on 2005-05-18
Hey all,

I want to add a few nice translucent overlays to a Blender animation I have created. However, when I try to open the avi in Kino, it tells me "Failed to load media file". I have tried rendering both "AVI Raw" and "AVI JPEG", but neither work.

I have also tried this

```
ffmpeg -i 0001_0780.avi -target dv gd.avi
```

... but no luck.

Any ideas?
Cheers

---

### Post by ubonetu on 2005-08-20
This does it for me:

```
ffmpeg -i candle.avi -target pal-dv candle.dv
``` 

or for other countries (or is it this country?):

```
ffmpeg -i candle.avi -target ntsc-dv candle.dv
``` 

Enjoy, I hope!

Ubonetu

---

### Post by Obscura on 2008-05-25
This is doing the trick but it's tedious to run against dozens of files.  Is there a way to run it against a directory full of avi files? 

I want to keep the original avi files.

---

