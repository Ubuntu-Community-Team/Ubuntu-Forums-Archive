---
title: "A Program For Converting Image Files"
date: 2008-07-03
forum: General Help
---

### Post by Mark76 on 2008-07-03
All I ever seem to do with Gimp is convert images from one filetype to another (and occasionally resize). It seems a bit of a waste to use a full featured graphics editing program for something so trivial. So is there something else I can use?

And please, not the CLI :lol:

---

### Post by linuxisfree on 2008-07-03
> **Mark76 said:**
> All I ever seem to do with Gimp is convert images from one filetype to another (and occasionally resize). It seems a bit of a waste to use a full featured graphics editing program for something so trivial. So is there something else I can use?

And please, not the CLI :lol:
 
You know, for converting images from 1 filetype to another, you can just use Eye of Gnome [EOG] (GNOME picture viewer). Just open the image with EOG and then click "Save As", then save as another filetype.

Hope that'll help!:D

---

### Post by erginemr on 2008-07-03
Eye of Gnome will do, but I can also recommend GThumb:
[http://gthumb.sourceforge.net/](http://gthumb.sourceforge.net/)

It is in the repositories:
```
sudo apt-get install gthumb
```

---

### Post by Barriehie on 2008-07-03
Gthumb will let you save as filename.xxx

---

### Post by dominiquec on 2008-07-03
ImageMagick is another suite of programs you should try.  It's command-line, but that makes it great for batch conversions.

```
sudo apt-get install imagemagick
```

This gives you programs like convert and mogrify.

For example, you can convert from JPEG to PNG using:

```
convert myimage.jpg myimage.png
```

You can also resize pictures, rotate, etc.  Very powerful.

---

### Post by linuxisfree on 2008-07-03
> **Barriehie said:**
> Gthumb will let you save as filename.xxx

So will EOG... (just saying) :D

---

### Post by dominiquec on 2008-07-03
D'oh! sorry, didn't see the "no CLI" requirement.  But the recommendation stands ;-)

---

### Post by manfer on 2008-07-03
You can install nautilus-image-converter extension too for scale and rotation (not valid for change the image format, for that purpose use the other alternatives mentioned). Then you can scale or rotate an image just right clicking on it in nautilus and selecting the operation from contextual menu.

If you use nautilus. Maybe you are not using gnome and not valid solution for you.

---

### Post by hyper_ch on 2008-07-03
> **dominiquec said:**
> D'oh! sorry, didn't see the "no CLI" requirement.  But the recommendation stands ;-)

a "no CLI" requirement cannot be applicable on linux ;) imagemagick is the way to go ;)

---

### Post by Mark76 on 2008-07-03
I have imagemagick.

It doesn't respond to ImageMagick imagemagick imagick Imagick or IMagick in a terminal. So it's a good job I have it in the menu.

---

### Post by kaibob on 2008-07-03
I use Imagemagick, but for a GUI what about phatch:

*Phatch is a simple to use cross-platform GUI Photo Batch Processor which handles all popular image formats and can duplicate (sub)folder hierarchies. Phatch can batch resize, rotate, apply perspective, shadows, rounded corners, ... and more in minutes instead of hours or days if you do it manually. Phatch allows you to use EXIF and IPTC tags for renaming and data stamping. Phatch also supports a console version to batch photos on webservers.*

[http://photobatch.stani.be/](http://photobatch.stani.be/)

---

### Post by Mark76 on 2008-07-03
And I can resize and rotate with Mirage.

---

### Post by kaibob on 2008-07-03
> **Mark76 said:**
> I have imagemagick. It doesn't respond to ImageMagick imagemagick imagick Imagick or IMagick in a terminal. So it's a good job I have it in the menu.

Imagemagick is a suite of command-line utilities. The one used to convert an image file to a different format is called convert:

[http://www.imagemagick.org/script/command-line-tools.php](http://www.imagemagick.org/script/command-line-tools.php)

---

### Post by Mark76 on 2008-07-03
Someone added a GUI :)

---

### Post by manfer on 2008-07-03
IMHO with a frontend for imagemagick you would be in the same situation as with gimp, an application doing too much for what you need. Anyway it would worth have a look at it.

Look the other options that people gave to you, only imagemagick was for the CLI, all the rest are GUI applications. For what I seen of them, Photo Batch Processor, looks very interesting application and suits for what you were looking for.

---

