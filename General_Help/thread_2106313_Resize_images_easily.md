---
title: "Resize images easily"
date: 2013-01-18
forum: General Help
---

### Post by samwillc on 2013-01-18
Hi,

I am looking for a way to quickly resize images for ebay stuff much the same way as you can on a mac when open in the default image viewer.

I was looking through the options in the default ubuntu 12.04 image viewer which is very nice and easy to use but although there is crop/rotate etc... no resize option.

Am I just missing something here or can this not be done in this program?

I didn't really want to install another image viewer as I hardly use them but will do if need be. I have not got to grips with gimp yet either as I am a long term adobe fireworks user and this is somewhat different, probably more similar to photoshop.

Anyway, any input is always appreciated. Thanks.

Sam.

---

### Post by ManamiVixen on 2013-01-18
Try Gthumb. It has a built in image rescale feature and is generally better than Shotwell. I use it. 
Just open it, use it's file browser to find your image, double click it to select it and open it, and then click tools<resize images

---

### Post by samwillc on 2013-01-18
> **ManamiVixen said:**
> Try Gthumb. It has a built in image rescale feature and is generally better than Shotwell. I use it. 
Just open it, use it's file browser to find your image, double click it to select it and open it, and then click tools<resize images

Ok thanks, I will give it a go :)

I must admit I didn't even realise shotwell was pre-installed until I typed it into the search bar a second ago!

Sam.

---

### Post by ibjsb4 on 2013-01-18
"nautilus-image-converter" extension to mass resize or rotate images
 
This package adds a "Resize Images..." menu item to
the context menu of all images. This opens a dialog
where you set the desired image size and file name.
A click on "Resize" finally resizes the image(s)
using ImageMagick's convert tool.

Its in the software center.

---

### Post by ajgreeny on 2013-01-18
> **ibjsb4 said:**
> "nautilus-image-converter" extension to mass resize or rotate images
 
This package adds a "Resize Images..." menu item to
the context menu of all images. This opens a dialog
where you set the desired image size and file name.
A click on "Resize" finally resizes the image(s)
using ImageMagick's convert tool.

Its in the software center.
+1
Easily the best way to do this quickly and painlessly.  I use it a lot!

---

### Post by samwillc on 2013-01-18
Top solution!

Will try that tomorrow.

Sam.

---

### Post by AstroLlama on 2013-01-18
if they all need to be resized to the same dimension a simple bash command will suffice:

This will resize all the files with .jpg extension in a folder to an image with a maximum dimension of 500px

```
 for file in *.jpg; do mogrify -resize 500x500 $file; done 
```

---

### Post by samwillc on 2013-01-18
Thanks for the hint but I would rather use some form of UI for this.

For a one-off job, the code would suffice but not for this.

Sam.

---

### Post by samwillc on 2013-01-19
> **ibjsb4 said:**
> "nautilus-image-converter" extension to mass resize or rotate images
 
This package adds a "Resize Images..." menu item to
the context menu of all images. This opens a dialog
where you set the desired image size and file name.
A click on "Resize" finally resizes the image(s)
using ImageMagick's convert tool.

Its in the software center.

Works brilliantly, so easy! Thanks :)

Sam.

---

### Post by jooge on 2013-03-17
> **ibjsb4 said:**
> "nautilus-image-converter" extension to mass resize or rotate images
 
This package adds a "Resize Images..." menu item to
the context menu of all images. This opens a dialog
where you set the desired image size and file name.
A click on "Resize" finally resizes the image(s)
using ImageMagick's convert tool.

Its in the software center.

Awesome Thx

---

