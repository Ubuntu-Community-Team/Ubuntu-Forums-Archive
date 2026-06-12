---
title: "Imagemagick bug?"
date: 2016-11-21
forum: General Help
---

### Post by g33zr on 2016-11-21
I've searched the forums and found only two related references to Imagemagick but one dates to 2008 and the other to 2010. 

Here's my issue: when I look for Imagemagick with Unity, two icons appear, but I click on either to launch the app, nothing happens. I've tried remove Imagmagick and its dependencies and then reinstalling, the same thing happens. Is anyone else having this problem? I've noticed that Imagemagick is "quirky" with other distros I've used and usually use either GIMP or Pinta instead, but I'd like to give Imagemagick another try if possible.

---

### Post by TheFu on 2016-11-22
imagemagick has a GUI?  Didn't know that.  Only used the imagemagick CLI tools.  Open a terminal and run the programs from there.  I only use a few of them - mainly 'convert' to optimize image sizes for websites and 'import' to capture screen areas.  The manpages for those say there is more information :
file:///usr/share/doc/ImageMagick-6/www/convert.html and 
file:///usr/share/doc/ImageMagick-6/www/import.html  

I see The Gimp (interactive and complex) and ImageMagick (batch) as different tools for very different purposes.

---

### Post by SeijiSensei on 2016-11-22
There is a GUI, but it's pretty useless.  For quick crops and resizing I use Gwenview, the KDE image viewer which has some nice features.  Otherwise I use the GIMP.

Imagemagick to me has always been most useful from the command line.  It's especially useful in scripts if you want to process all the images in a directory.  For instance, making thumbnails:
```

mkdir thumbs
mogrify -path thumbs -thumbnail 200 -format png *.jpg
```
That takes all the JPEG images in the current directory and creates PNG thumbnails for each of them with a horizontal width of 200 pixels.  The height is chosen to match the aspect ratio.  It puts all these images in the "thumbs" subdirectory.

---

### Post by vasa1 on 2016-11-22
I got updates for imagemagick today:```
Upgrade: imagemagick:amd64 (8:6.8.9.9-7ubuntu5.1, 8:6.8.9.9-7ubuntu5.2), libmagickwand-6.q16-2:amd64 (8:6.8.9.9-7ubuntu5.1, 8:6.8.9.9-7ubuntu5.2), imagemagick-6.q16:amd64 (8:6.8.9.9-7ubuntu5.1, 8:6.8.9.9-7ubuntu5.2), libmagickcore-6.q16-2-extra:amd64 (8:6.8.9.9-7ubuntu5.1, 8:6.8.9.9-7ubuntu5.2), libpulse0:amd64 (1:8.0-0ubuntu3, 1:8.0-0ubuntu3.1), libpulse-mainloop-glib0:amd64 (1:8.0-0ubuntu3, 1:8.0-0ubuntu3.1), tar:amd64 (1.28-2.1, 1.28-2.1ubuntu0.1), libmagickcore-6.q16-2:amd64 (8:6.8.9.9-7ubuntu5.1, 8:6.8.9.9-7ubuntu5.2), imagemagick-common:amd64 (8:6.8.9.9-7ubuntu5.1, 8:6.8.9.9-7ubuntu5.2)

``````
$ apt-cache policy imagemagick
imagemagick:
  Installed: 8:6.8.9.9-7ubuntu5.2
  Candidate: 8:6.8.9.9-7ubuntu5.2
  Version table:
 *** 8:6.8.9.9-7ubuntu5.2 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     8:6.8.9.9-7ubuntu5 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
$ 
```

I'm not using Unity but I guess the .desktop files are the same. There are two in */usr/share/applications*. As you've reported with your system, double-clicking on them doesn't launch anything.

Then I looked at their "Exec=" lines. The smaller file (982 bytes) had```
/usr/bin/display-im6 %f
```and the other (1020 bytes) had```
/usr/lib/x86_64-linux-gnu/ImageMagick-6.8.9/bin-Q16/display %f
```For what it's worth, both commands seem to work from the command line.

The GUI seems to be some sort of X-windows thing. I don't use imagemagick via the GUI myself or I'd have to first figure out how to change the yellow lettering to something easier to read.

---

### Post by g33zr on 2016-11-22
Thanks to all of you for your comments. It's not the kind of program I need or use, so I'll stick to what I've got and add Darktable.

---

### Post by g33zr on 2016-11-22
Update: seeing that I don't intend to use Imagemagick, I decided to remove it and was most surprised to discover that removing it removed my printer settings, including cups. I not only had to reinstall the app but the dependencies as well. Apparently, I need it after all. :rolleyes:

---

### Post by vasa1 on 2016-11-23
> **g33zr said:**
> Update: seeing that I don't intend to use Imagemagick, I decided to remove it and was most surprised to discover that removing it removed my printer settings, including cups. I not only had to reinstall the app but the dependencies as well. Apparently, I need it after all. :rolleyes:
```
apt-get purge -s some_package
```gives one a simulation of what could happen if one were to remove "some_package".

---

