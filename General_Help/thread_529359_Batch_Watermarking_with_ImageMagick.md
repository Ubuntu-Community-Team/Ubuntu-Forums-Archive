---
title: "Batch Watermarking with ImageMagick?"
date: 2007-08-19
forum: General Help
---

### Post by neilrizo on 2007-08-19
I found a command on ImageMagick that lets me place watermarks on my photos (refer to the line and URL below). To do this on my photos one at a time is a bit tedious.

Is there a way to alter the command below so that i can batch edit my photos? Maybe have the option of overwriting the filenames or making entirely new ones.


[http://www.imagemagick.org/Usage/annotating/#wmark_image](http://www.imagemagick.org/Usage/annotating/#wmark_image)

composite -watermark 30% -gravity south \
             wmark_image.png  logo.jpg    wmark_watermark.jpg


NOTE: I couldn't figure out how to put the code in a box. Sorry about that.

---

### Post by Swarms on 2007-08-19
Use this program, its excellent for doing commands to a whole folder.
[https://launchpad.net/phatch](https://launchpad.net/phatch)

---

### Post by bashologist on 2007-08-19
Be careful and make backups first. If you're using a glob remember that it could be written to overwrite your watermark logo thing. Find a good bash tutorial that'll teach you the basics about for loops and globs or maybe use some program like Swarms suggested.

---

