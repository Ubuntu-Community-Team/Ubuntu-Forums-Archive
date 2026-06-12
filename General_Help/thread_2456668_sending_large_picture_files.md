---
title: "sending large picture files"
date: 2021-01-16
forum: General Help
---

### Post by wmrp on 2021-01-16
What is the easiest way to make picture files smaller for emailing photos? I am running Ubuntu 20.04.

---

### Post by HermanAB on 2021-01-16
Imagemagick convert can do it:
$ man convert

---

### Post by wmrp on 2021-01-16
> **HermanAB said:**
> Imagemagick convert can do it:
$ man convert

Is that part of Ubuntu 20.04, and I just write man convert in the terminal? (sorry; I am new at Linux)

---

### Post by wmrp on 2021-01-16
> **wmrp said:**
> Is that part of Ubuntu 20.04, and I just write man convert in the terminal? (sorry; I am new at Linux)


$ man convert
No manual entry for convert

---

### Post by T6&amp;sfpER35% on 2021-01-16
[https://developpaper.com/how-to-install-and-use-imagemagick-software-in-linux-system/](https://developpaper.com/how-to-install-and-use-imagemagick-software-in-linux-system/)

---

### Post by T6&amp;sfpER35% on 2021-01-16
if you new to linux you might struggle with command line and resizing through it
try gimp
go to **file - open** and open the image then **image** and **scale image** then **file** - **export as**

---

### Post by wmrp on 2021-01-16
I have GIMP installed and opened the pictures in there, but I haven't yet found the option of reducing their bit size.

---

### Post by wmrp on 2021-01-16
> **3nd said:**
> if you new to linux you might struggle with command line and resizing through it
try gimp
go to **file - open** and open the image then **image** and **scale image** then **export as**

Oh, looks like we were posting simultaneously! Thank you so much; that is the info I was looking for! :-)

---

### Post by wmrp on 2021-01-16
> **3nd said:**
> if you new to linux you might struggle with command line and resizing through it
try gimp
go to **file - open** and open the image then **image** and **scale image** then **file** - **export as**

What is a pretty reasonable size if I want to email a few pictures? It scales height and width separately for some reason.

---

### Post by wmrp on 2021-01-16
> **wmrp said:**
> What is a pretty reasonable size if I want to email a few pictures? It scales height and width separately for some reason.

I accidentally clicked on the chain that disconnected width and height. Corrected it now. I am on a roll now. Thanks again!

---

### Post by ajgreeny on 2021-01-16
You therefore do not already have it installed and need to run command ```
sudo apt install imagemagick
``` which will do the trick.

Imagemagick is the "Swiss knife" of image editing and can do juat about anything; convert is just one of the many executables it provides as you will see if you run ```
man imagemagick
```, but is entirely command line so don't expect to see a GUI.

EDIT:
Too many simultaneous posts, including this one!

If you need a GUI application and want something smaller than gimp have a look at nomacs; it's much quicker and simpler than gimp but will manage several image edits quite easily using the **Adjustments** menu

---

### Post by SeijiSensei on 2021-01-16
> **wmrp said:**
> What is a pretty reasonable size if I want to email a few pictures? It scales height and width separately for some reason.
If you accept the defaults in GIMP, it will scale the picture proportionally along both axes.  Type a number like 400 in the width box from the Image > Scale Image dialog and the height will adjust accordingly. You can change each axis independently if you click on the little chain icon to unlock height and width, but then the image will be distorted.

If the image seems too small after downscaling, hit the "1" key to zoom to 100%. 

How big is too big depends on your recipient. If they have poor internet connectivity, then you want to make the images smaller.  I maintain a photo gallery site for my college classmates and have standardized on a 400 pixel width in portrait view for all the pictures.  The largest files are about 250K which isn't that big by modern-day standards.  They all look fine.  If you expect your recipient to be printing these images, then you want to go bigger to enable better resolution on the printer.  You might use widths of 1600px or more in those cases if your original images are larger than that.  Never scale up an image if you can help it. Upscaling creates "information" by inventing extra pixels that are shaded depending on those surrounding it.

---

### Post by andrew.46 on 2021-01-17
If you are keen to try the command line as others have suggested there is a* very simple* way to use imagemagick and resize your image based on the percentage point of your choice.  For example to reduce the size of your image by 50%:

```

convert big_image.jpg -resize 50% smaller_image.jpg

```

There are many ways to accomplish this goal with imagemagick but this is perhaps the easiest.

---

### Post by malspa on 2021-01-17
I use ***nomacs*** ([https://packages.ubuntu.com/focal/nomacs](https://packages.ubuntu.com/focal/nomacs)). It has a super-easy way to reduce image sizes. I open the image in nomacs, then click *File > Save for Web*. There's another step that shows part of the original and new images; I click *OK* and then attach the resulting image to the email message.

---

### Post by ActionParsnip on 2021-01-17
You can use imagemagick to reduce quality and make the files smaller that way. You can also shrink the size and make them smaller that way too

---

### Post by malspa on 2021-01-17
> **ActionParsnip said:**
> You can use imagemagick to reduce quality and make the files smaller that way. You can also shrink the size and make them smaller that way too

Yeah, "HemanAB" mentioned imagemagick in the first reply.

---

### Post by TheFu on 2021-01-17
$ more bin/img-opt.sh 
```
#!/bin/bash
QUAL=40

for img in "$@"; do
  NEW=${img/%.???/-opt.jpg}
  echo " Working on $img ..."
   convert -quality $QUAL  "$img"  "$NEW"
done

```
That's an example script to use **convert**. JPG files can be drastically reduced in size with almost zero notice to humans in the quality for a specific size.  10x reductions are easy.

That script can create new jpg files provided as input to be 10x or more smaller.

Run it:
```
$ img-opt.sh *jpg
```
or gif or png or ... but the output will always be jpg files.  1,5, 200 fles - no problem.

---

### Post by kel008 on 2021-01-18
> **wmrp said:**
> What is the easiest way to make picture files smaller for emailing photos? I am running Ubuntu 20.04.

My first post: I have found that imagemagick is the best for this task. But you don't have to use it from the command line. You can use it in your default GUI file manager 'Nautilus'. From the terminal do:

sudo apt install imagemagick
sudo apt install nautilus-image-converter
nautilus -q # Reloads nautilus configuration

Once you have done this you should be able to point to any picture file and right click for the option to resize the file or files (it will do bulk resizes).

This thanks to: [https://askubuntu.com/questions/1053081/how-to-install-the-right-click-photo-resizer-on-ubuntu-18-04](https://askubuntu.com/questions/1053081/how-to-install-the-right-click-photo-resizer-on-ubuntu-18-04)

Cheers,
Mike

---

### Post by TheFu on 2021-01-19
kel008, good method for many.  

Also, there is a very old-school GUI for most ImageMagick tools - it looks like X-Apps from 1993. Sorta like the image next to my posts (xman). Basically, it is a launcher for all the ImageMagick tools with input fields for each as make sense. I always find it odd how people are willing to mouse and fill out a simple set of fields for a program rather than provide command options with exactly the same meaning in a shell.  

Plus, in a shell we can put commands and options used into a file to be 5, 500, 500000, 5Q times. Much quicker, especially when using tab-command-completion.  People moving from Windows often don't know about tab-completion which prevents users from typing more than 2-3 characters for options or filenames.

---

