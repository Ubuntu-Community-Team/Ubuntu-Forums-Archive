---
title: "File format"
date: 2014-12-02
forum: General Help
---

### Post by Peter Ratcliffe on 2014-12-02
A file clola.pdf came with an e-mail.  This a scan of a photograph.  I took it to my local photogrphy shop to get a print, but their machine can't read this file.  They say it has to be in fpeg format.  Is it possible to reformat a file from .pdf tp .jpg?

Advice will be appreciated.

Peter Ratcliffe

---

### Post by howefield on 2014-12-02
You could use imagemagick or the gimp. There are a bunch of threads already in the forum such as ...

[http://ubuntuforums.org/showthread.php?t=993370](http://ubuntuforums.org/showthread.php?t=993370)
[http://ubuntuforums.org/showthread.php?t=1965114](http://ubuntuforums.org/showthread.php?t=1965114)

---

### Post by slickymaster on 2014-12-02
Install [imagemagick]("http://apt.ubuntu.com/p/imagemagick"), then open a terminal window and run the following:```
convert /path/to/name_of_file.pdf -quality 100 /path/to/name_of_file.jpg
```

Alternatively, if you have GIMP in your computer, it is capable of using PDFs, i.e. converting them into images. So if you want to edit the images right away - GIMP is your friend.

_**EDIT:**_ howefield beat me :p

---

### Post by Impavidus on 2014-12-02
Images can be stored in pdf in many different ways. If it's a scanned image, it is most likely either uncompressed (making a very large file) or using the same compression algorithm as jpeg. In this case, it can be losslessly converted into jpeg, hardly changing the file size, by just changing the metadata and header into those of a jpeg file, without changing the image data. I don't think gimp is smart enough to do this, but convert (part of imagemagick) may.

---

### Post by Peter Ratcliffe on 2014-12-06
Thanks guys.  GIMP worked a treat

---

