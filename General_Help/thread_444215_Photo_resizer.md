---
title: "Photo resizer?"
date: 2007-05-15
forum: General Help
---

### Post by Man_Beach on 2007-05-15
There is a rather useful little freeware programme for windows which my wife uses a lot to resize jpg photographs before emailing them. It's called Picture Resizer from [http://www.rw-designer.com/picture-resize](http://www.rw-designer.com/picture-resize) and consists of an icon on the desktop. She just drags her images onto it and it produces a smaller copy in the same directory with the suffix -800 added after - I've got it set so that the maximum dimension is 800 pixels - so that picture.jpg is renamed picture-800.jpg

She uses it a lot  - it's so simple and you can't go wrong with it - and I'd like to produce something similar on the Ubuntu desktop (possibly using convert -resize?) which she could use instead of her rebooting into windows all the time to do picture resizing. Could anyone give me some ideas? I know nothing about scripts, etc. but don't mind trying.

---

### Post by kidders on 2007-05-16
Hi there,

As you suggested, ImageMagick is the way to go, imo. Essentially, it'd be a case of doing something like this...
```
convert -resize ">800x" big_image.png big_image-800.jpg
```I'm assuming the reason for down-sizing photos is web-related, so by specifying different extensions for input & output, you can have ImageMagick convert less common image formats (eg TIFF images) to JPEGs or PNGs, while it's resizing.

Here's one suggestion...
```
#!/bin/bash
NEWNAME="${1%\.*}-800.jpg"
convert -resize ">800x" "$1" "$NEWNAME"
```Since you'd be going to the trouble of making a script though, there's no reason not to get a little more ambitious...

```

if [ -d "$1" ]; then
     echo "Converting entire directory..."
     ...
     ...
else
     echo "Converting single file..."
     ...
     ...
fi
```Whatever you choose to do, I would suggest saving your script as something like /usr/local/bin/picture-resize, and (assuming you're using Gnome) creating a launcher on your desktop to drop files and/or directories onto.

_**One quick note**_
Shell scripts can be a little dangerous. One simple (and perhaps silly) example is that a malicious local user might try to add **rm -Rf ~** to your script, causing it to erase your entire home directory when you next invoke it. From a security perspective, it is important to do the following, as a matter of good practice...[LIST]
[*]sudo chown root:root /user/local/bin/picture-resizer
[*]sudo chmod 755 !$[/LIST]
Since you're not very familiar with scripting, I would recommend going slowly & carefully, when writing things that create & modify files. (It's remarkably easy to do quite a lot of damage!) _Never run a script as root_ unless absolutely necessary. Quite often, I like to temporarily precede commands I'm unsure about with **echo**, so I can see what *would* be executed, rather than actually doing it.

I hope that gives you some ideas.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by Man_Beach on 2007-05-18
Thank you kidders. I'll give it a go and post back if I have problems, but everything seems clear enough.

[The reason for reducing the size of the pictures is simply that she might have to email 8 or 9 photos to someone - and 8 at 80kb is better than 8 at 400kb! (Some people don't like getting 3mb of attachments)]

---

### Post by fragos on 2007-05-18
This can also be done fairly simply with gThumb.  She can click her image and gThumb will open with it or you can place a gTumb icon on the desktop and she can drag to it.  In the opened image she selects Tools from the menu line and then Scale images...  Next click the Scale button and you'll be prompted for a new name.  IMHO -- This is more user friendly and safer than a script.

---

