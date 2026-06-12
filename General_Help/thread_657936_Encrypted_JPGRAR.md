---
title: "Encrypted JPG/RAR"
date: 2008-01-04
forum: General Help
---

### Post by FuturistCorporation on 2008-01-04
I have a jpg image with a rar file encrypted in it. Is there any way I can convert .jpg file type to .rar?

---

### Post by icheyne on 2008-01-04
How was it inserted in the jpg? Something like this? [http://lifehacker.com/software/encryption/hide-files-in-jpeg-images-207905.php](http://lifehacker.com/software/encryption/hide-files-in-jpeg-images-207905.php)

Rename the file to filename.rar?
Maybe try to open the image with Ark?

---

### Post by FuturistCorporation on 2008-01-08
Yes it's been inserted through DOS command like that. However, when I rename the file extension to .rar, Ubuntu still reads it as a jpg. The file type under properties still says I've got an image file.

Also what is Ark?

---

### Post by icheyne on 2008-01-08
In that case, you have to unrar (decompress) the file. Ark is the Ubuntu archiver - you can use it to decompress. You will have to install unrar to make it work. Use Synaptic to install unrar.

---

### Post by Parkbench on 2008-07-11
I have a heap of jpeg/rars, when I open them (in hardy) I just change it from filename.jpg to filename.rar, rightclick, open with, find archive manager, and open with that.

But you need to make sure that archive manager supports rar and zip files. If not, go to synaptic, search for unrar, install that. OR you can do the following in a terminal:

```
sudo apt-get install unrar
```

Now I'm wondering if I can make new jpeg/rars in ubuntu, i used to make heaps in XP. If anyone knows how, let me know.

---

