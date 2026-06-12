---
title: "wget and live streams"
date: 2007-05-24
forum: General Help
---

### Post by martinrandau on 2007-05-24
I am looking for way/script to download all files in a directory that is accessible through streaming.

Specifically I want to download all of the files in [http://www.archive.org/details/gd71-12-14.sbd.deibert.12763.sbeok.shnf](http://www.archive.org/details/gd71-12-14.sbd.deibert.12763.sbeok.shnf)

I can do it file-by-file by playing the stream in totem, clicking "copy location" for each file and then do, eg ```
wget http://www.archive.org/download/gd71-12-14.sbd.deibert.12763.sbeok.shnf/gd1971-12-14d1t01_vbr.mp3
```

But this is tedious and takes a lot of time.

Question: How can I get wget to download all of the files in [http://www.archive.org/download/gd71-12-14.sbd.deibert.12763.sbeok.shnf/](http://www.archive.org/download/gd71-12-14.sbd.deibert.12763.sbeok.shnf/) ?

Any tips appreciated!

Note: Downloading these files is not illegal!

---

### Post by aktiwers on 2007-05-24
> wget -r -np -A mp3 -l 2 [http://www.archive.org/download/gd71-12-14.sbd.deibert.12763.sbeok.shnf/](http://www.archive.org/download/gd71-12-14.sbd.deibert.12763.sbeok.shnf/)-r stands for recursivly
-l 2 is for two levels of recursion (this is to avoid to download too much, since wget recurces through links..)
-np no parent folders
-A mp3 only wma files

But the link seams dead to me.

---

