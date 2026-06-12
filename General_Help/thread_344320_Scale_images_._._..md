---
title: "Scale images . . ."
date: 2007-01-22
forum: General Help
---

### Post by kolinab on 2007-01-22
I've been looking for a simple, fast way of resizing batches of images. The solution I found was to use a nautilus script to do the work for me. So . . . 

I downloaded the scripts at [http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/) and dropped them into my .gnome2 directory. The scripts all appear in my 'scripts' menu, and when I select the 'scale images' script,  things appear to be working - but once I select my size option and click apply, the window goes away and my images don't resize. Maybe I need to install something else to make these scripts work?

I'm totally open to different options - maybe a small image resize program or something? I just want to resize pics in batches for emailing to folks, etc.

[edit]

So this is easy to do in Gthumb, as I have discovered. But still no hints as to why the scripts don't work.

---

### Post by aysiu on 2007-01-22
I don't know why the script isn't working, but I did want to let you know that *imagemagick* is also another great way to batch resize:
[http://www.imagemagick.org/script/command-line-processing.php](http://www.imagemagick.org/script/command-line-processing.php)

> 
Inline Image Resize
    It is sometimes convenient to resize an image as they are read. Suppose you have hundreds of large JPEG images you want to convert to a sequence of PNG thumbails: ```
 convert '*.jpg' -resize 120x120 thumbnail%03d.png
``` Here all the images are read and subsequently resized. It is faster and less resource intensive to resize each image as they are read: ```
convert '*.jpg[120x120]' thumbnail%03d.png
```

---

### Post by kolinab on 2007-01-23
Thanks for the tip Aysiu. I've not used scripts before so I'll do some reading tonight to learn some ins and outs. 

I'm having a look at that Imagemagick - it certainly looks like a really powerful tool!

---

### Post by stani on 2007-12-21
Try Phatch (photo batch processor): [http://photobatch.stani.be](http://photobatch.stani.be)

---

