---
title: "looking for a way to batch convert 128X128 pngs into other sizes (96,22 etc..)!"
date: 2006-11-20
forum: General Help
---

### Post by zeltak on 2006-11-20
Hi guys

i have loads of cool mimetypes i made/downloaded in 128X128 size format. i want to use the in kubuntu and am looking for a way/program to batch convert each png  which is in 128X128 into the same png image but in different sized (96,72,56,22 etc..) does anyone know how to do this?

thx alot in advance

Zeltak

---

### Post by earobinson on 2006-11-20
you should be able to use the convert command to do this. It if it is not installed install imagemagic

---

### Post by zeltak on 2006-11-20
cool!

does anyone know where i can get a .deb file for this? i dont know how to compile and it isnt in apt-get?

thx 

Zeltak

---

### Post by kno712 on 2006-11-20
It is in the repos; try again. It is 'imagemagick' (don't forget the 'k' at the end); it is a command line tool, but very powerfull; do a google search to find the web site and find out all the commands and options.

---

### Post by earobinson on 2006-11-22
I dont think its in the stock repos you need to to get the full repo set to install it

---

### Post by Peepsalot on 2006-11-22
Yeah I think you want to use imagemagick convert command with the -resize option. 

Here is the documentation on the imagemagick library.
[http://www.imagemagick.org/script/command-line-tools.php](http://www.imagemagick.org/script/command-line-tools.php)

I may be wrong but I think it comes installed by default on ubuntu.  Try running "convert --help" in terminal.

---

### Post by Qew on 2006-11-22
The package imagemagick (do remember the k at the end) is certainly in the official repos.

Anyway, when doing batch conversion, you'll want the "mogrify" command. Use "mogrify -resize 96x96 *.png" to make the changes. It might be best to copy the original files to another directory and work there, so you don't overwrite your original files. Also, you might want the -thumbnail switch instead of the -resize one for such small images. Obviously you can look at man mogrify to look up any further things you'll need to consider. [This is another reference to mogrify.](http://www.imagemagick.org/script/mogrify.php)

---

### Post by stani on 2007-06-01
I've started to work on a new graphic program especially designed for photo batching with a graphical user interface (GUI).  The first version will be fairly simple, no preview yet and only a few plugins (scale, rotate, save, invert, ...). I originally develop it for Ubuntu, but I might port it to Windows and Mac in the future. Progress is going fine, so beta testers will be welcome. If someone is interested in beta-testing my program at a later stage, please send me a private message with your email.
Stani

Everyone with knowledge of PIL (Python Image Library) can easily write plugins for it. There is no need for GUI programming, as my program will take care of it. So anyone who wants to write a plugin (as simple as rotate, invert, contrast, ...) please contact me as well.
--
[http://pythonide.stani.be](http://pythonide.stani.be)

---

### Post by stani on 2007-06-06
The very first alpha version of my photo batch processor is available for testing:
[http://ubuntuforums.org/showthread.php?t=466598](http://ubuntuforums.org/showthread.php?t=466598)

---

