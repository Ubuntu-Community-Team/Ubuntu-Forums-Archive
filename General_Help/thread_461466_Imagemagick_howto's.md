---
title: "Imagemagick howto's"
date: 2007-06-01
forum: General Help
---

### Post by eentonig on 2007-06-01
Does anybody have some link where I could find some decent howto's regarding Imagemagick?

---

### Post by RedSquirrel on 2007-06-01
I would consult the ImageMagick home page

[http://www.imagemagick.org](http://www.imagemagick.org)

and specifically this page:

[http://www.imagemagick.org/Usage/](http://www.imagemagick.org/Usage/)

---

### Post by eentonig on 2007-06-02
I've already done that.

The problem is that a lot of command they show there, are not known in the version that comes with Ubuntu.

---

### Post by ricardisimo on 2007-06-05
I'd even like to step back a few kilometers and ask which download from their site is appropriate to Ubuntu, and how to install it.

---

### Post by eentonig on 2007-06-07
It's in the repo's. You don't need to install it from their website.

> sudo apt-get install imagemagick

---

### Post by ricardisimo on 2007-06-08
Oh, damn... I think I may have even already had it installed and didn't even know it. OK, so back to your question: where can I get more detailed instructions? I'd like to know how to grab an entire folder of JPGs and GIFs and convert them to both PNGs and SVGs, preferably simultaneously and exporting them to separate folders.

This might be too much to ask, but would adding a left-click "convert" option to my mouse when it's dragged over an image file be too much to ask as well? Thanks in advance.

---

### Post by Waldo323 on 2007-09-06
> **ricardisimo said:**
> Oh, damn... I think I may have even already had it installed and didn't even know it. OK, so back to your question: where can I get more detailed instructions? I'd like to know how to grab an entire folder of JPGs and GIFs and convert them to both PNGs and SVGs, preferably simultaneously and exporting them to separate folders.

This might be too much to ask, but would adding a left-click "convert" option to my mouse when it's dragged over an image file be too much to ask as well? Thanks in advance.

it is possible to do this. I haven't found something that already converts images to 2 different images types in a separate directory.

from the sites I found during my search it looks like you would need to do a couple things to get this to work.

I'll paste a couple reference sites and if I come up with something that does exactly what you want, I'll post again.

You can use the first as an example of a nautilus script and use the convert information from the second for information about how to convert each selected image to png and use autotrace to convert to svg(you'll prolly need to add arguments to make it work correctly) and change the desired location of the output files in the bash script (possibly make the directory if it does not exist yet)

to resize images from nautilus 
[http://www.creationgif.com/debian/nis/](http://www.creationgif.com/debian/nis/)

how to convert to png using imagemagick
[http://www.imagemagick.org/www/convert.html](http://www.imagemagick.org/www/convert.html)

$ convert image.jpg image.png


autotrace's sourceforge page, its likely in the ubuntu repos to install
[http://autotrace.sourceforge.net/](http://autotrace.sourceforge.net/)

---

### Post by pundip on 2007-10-25
Does anyone know where the path to imagemagick is in ubuntu 7.10. I have a web app that is asking for the path and i cant seem to find this information.

---

### Post by newOldUser on 2007-12-10
If I understand it correctly imagemagick is made up of multiple modules and imagemagick is the collective name of the package of modules. One of the executable  modules is called "composite".  To find where "composite" has been installed use the command "whereis".

In a terminal window enter the command:
whereis composite

On my machine it responds:
/usr/bin/composite

---

