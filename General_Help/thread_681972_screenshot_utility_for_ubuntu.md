---
title: "screenshot utility for ubuntu"
date: 2008-01-29
forum: General Help
---

### Post by banda on 2008-01-29
i stopped using compiz in ubuntu, so i had to look for a screenshot utility as awesome as the one that comes with compiz.

the default one on ubuntu lacks the ability to take a shot of specified area/window or saving it in .jpg format.

basically i do a lot of screenshots and opening photoshop/gimp everytime to convert to jpg and crop them is not very comfortable

i found one application called 'scrot', but it has a drawback.. it lacks a ui.

but with a few parameters attached to it in the command line it does exactly what i want it to do , thought i'd share how i did it...

get scrot installed 1st
> sudo apt-get install scrot

next, save a file with the following contents in it and save it somewhere, rename it to something.
make it executable
> #!/bin/sh

scrot '$pscreenshot.jpg' -s -q '85' -e 'mv $f ~/Desktop/'

to make it more accessible put a launcher for '/somewhere/something' on the top bar

now whenever you click on the launcher, you can make a selection square on the screen and a picture of that region would pe put on your desktop,
or you can just click the titlebar of a window to save a picture of a single window.

be careful though, if you take another picture of exactly the same dimensions, you will loose the previous one

---

### Post by K.Mandla on 2008-01-30
Moved to General Help.

---

### Post by jimcooncat on 2008-01-30
I made this script, and put it on my panel as a launcher. I click the launcher, and the mouse cursor changes to a + sign. Using that, I highlight the area of my screen, and it dumps a .png on my desktop. I use it many times daily.

This script used the import utility from ImageMagick. So, before using,

```
sudo aptitude install imagemagick
```

The script:
```
#! /bin/bash
timestamp=`date +%d%m%y_%H%M%S`;
import ~/Desktop/screenshot_$timestamp.png;

```

---

