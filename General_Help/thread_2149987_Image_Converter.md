---
title: "Image Converter"
date: 2013-05-30
forum: General Help
---

### Post by borgward on 2013-05-30
Is there a program that converts images to another format, or reduces their size?

---

### Post by MartyBuntu on 2013-05-30
GIMP does all that and more.

---

### Post by The Cog on 2013-05-30
package imagemagick. It's in the repositories. The binaries of most interest are convert and mogrify. Something like
convert --resize 800x600 *.mpg 
The list of options ann things it can do is amazingly long.
I believe there are graphical front-ends too, but I haven't used them.

---

### Post by ajgreeny on 2013-05-30
If you are using nautilus you can install **nautilus-image-converter** or **nautilus-image-manipulator** to resize images with a right click; very quick and convenient.

For changing the image file-type, eg png to jpg or to resize in the command line, as The Cog says, you should look at imagemagick; dead easy to use, and also very quick.

---

### Post by Buntu Bunny on 2013-05-30
> **MartyBuntu said:**
> GIMP does all that and more.

+1 for Gimp

---

### Post by ajgreeny on 2013-05-30
> **Buntu Bunny said:**
> +1 for Gimp

But that is a huge application just to resize an image or to convert it from one file-type to another.

Overkill?  I think so.

---

### Post by CaptainMark on 2013-05-31
Agreed, Gimp is good but this is a bit like using a sledgehammer to crack a nutshell. Totally overkill, but if you want a one stop shop for all your image manipulation needs I don't think anyone here would up much argument against gimp

---

### Post by sudodus on 2013-05-31
> **The Cog said:**
> package imagemagick. It's in the repositories. The binaries of most interest are convert and mogrify. Something like
convert --resize 800x600 *.mpg 
The list of options ann things it can do is amazingly long.
I believe there are graphical front-ends too, but I haven't used them.

+1

Particularly if you want to run a batch job for several pictures, imagemagick convert is good. There are good tutorials on the internet. For single or a few pictures the gimp is good (as stated above).

---

### Post by coffeecat on 2013-05-31
@borgward, you don't say whether you want to do single image or batch conversion/resize. Another GUI app which is good at both and which is worth a look is gThumb. It has a few simple image manipulation tools and, although I routinely install both it and gimp, I tend to prefer gThumb for simple jobs such as cropping images.

---

### Post by borgward on 2013-05-31
I just want to reduce the file size of a single .jpg so I can post it to a particular site that has a size limitation.

---

### Post by HiImTye on 2013-05-31
> **borgward said:**
> I just want to reduce the file size of a single .jpg so I can post it to a particular site that has a size limitation.
install imagemagick
```
sudo apt-get install imagemagick
```
convert one image
```
convert -quality 95 /path/to/infile.ext /path/to/outfile.png
```
batch converting
```
convert -quality 95 /path/to/files/*.ext /path/to/outfiles/%04d.png
```
will numerically name them up to 9999, use %05d for up to 99999
more info on PNG compression:
[http://www.imagemagick.org/Usage/formats/#png_quality](http://www.imagemagick.org/Usage/formats/#png_quality)
[http://www.imagemagick.org/script/command-line-options.php#quality](http://www.imagemagick.org/script/command-line-options.php#quality) [CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by Juniorr on 2013-05-31
> **Buntu Bunny said:**
> +1 for Gimp
+2, it's the best out there, really easy to use and really quality program, I do all my editing on it.

---

### Post by gifford on 2013-05-31
Converseen,[http://www.noobslab.com/2012/02/install-converseen-image-converter-on.html](http://www.noobslab.com/2012/02/install-converseen-image-converter-on.html)
Trimage image compressor, in Ubuntu software center.
Both are fairly easy to use and compact.

---

### Post by CaptainMark on 2013-06-01
In that case use gthumb, installed by default (I believe), find a picture on your pc and use the button "Tools" > "Resize Images" to change the resolution, you can work out the correct percentage to scale by by using the current image size compared to what you want it to be

---

### Post by ajgreeny on 2013-06-01
I still believe that the **nautilus-image-converter** would be the simplest way for you.

How can anything be simpler than a right click on the file or files in nautilus and "Resize images"?

---

### Post by borgward on 2013-06-01
I tried both.  GThumb is very easy, but nautilus-image-converter is easier. I have both Nautilus and Nemo on my laptop. I had to search to find Nautilus as I have always used Nemo.  Gimp is a great program, but overkill for what I wanted to do.

---

### Post by shakma on 2013-06-09
> **ajgreeny said:**
> If you are using nautilus you can install **nautilus-image-converter** or **nautilus-image-manipulator** to resize images with a right click; very quick and convenient.

For changing the image file-type, eg png to jpg or to resize in the command line, as The Cog says, you should look at imagemagick; dead easy to use, and also very quick.

+1 for nautilus-image- tools.  Gimp is awesome, but being able to right-click and resize an image is totally fresh!

Peace.

---

