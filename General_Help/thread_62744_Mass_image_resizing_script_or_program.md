---
title: "Mass image resizing script or program?"
date: 2005-09-05
forum: General Help
---

### Post by drews_blunted on 2005-09-05
Hey so i just got back from norway after a wounderful 2 weeks there. I am wondering if anyone know a good script or program i can use to convert all my images that are in a huge resolution to 800x600 for easy viewing? Im going to need to convert some 400+ pictures. Hopefully a perl script or something can take care of this! Thanks! :)

---

### Post by arnieboy on 2005-09-05
[QUOTE=drews_blunted]Hey so i just got back from norway after a wounderful 2 weeks there. I am wondering if anyone know a good script or program i can use to convert all my images that are in a huge resolution to 800x600 for easy viewing? Im going to need to convert some 400+ pictures. Hopefully a perl script or something can take care of this! Thanks! :)[/QUOTE]
[http://ubuntuguide.org/#bbips](http://ubuntuguide.org/#bbips)

---

### Post by bdamon on 2005-09-06
[QUOTE=drews_blunted] I am wondering if anyone know a good script or program i can use to convert all my images that are in a huge resolution to 800x600 for easy viewing? Im going to need to convert some 400+ pictures.[/QUOTE]

I created my own shell script that uses imagemagick to do something similar.

```

#!/bin/bash
for i in `ls *.jpg`;
do
	convert $i -resize 800x600 $i
done
```

This assumes your files have a .jpg extension and will work on all files in the directory it is run from. You can also specify a percentage to resize as well 

-resize 40%

A word of caution make a backup of your files and make sure to test the script before you use it.

---

### Post by Cordate on 2005-12-28
It took me a bit of experimenting to figure out how to get this to work for me. Here's a couple of pointers:

1) You'll need Imagemagic installed.

2) The script won't work on filenames with spaces in them. Use dashes or underscores instead (eg: use "cool-photo.jpg" or "cool_photo.jpg", not "cool photo.jpg"). You can always mass-rename them afterward if you want the hard-to-work-with filenames :)

---

