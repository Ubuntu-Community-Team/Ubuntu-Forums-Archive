---
title: "Tiff image file opens in Windows but not in Ubuntu"
date: 2013-09-18
forum: General Help
---

### Post by Petro Dawg on 2013-09-18
I have a couple really long .tif files.  They are well Logs to be exact and I would guess each around 400 pixels wide and at least 40000 pixels high.  The default image viewer in Windows (on another computer) was able to view them without issue, but I'm having a hard time opening them in Ubuntu 12.04.  

"Image Viewer" returns an error stating that the image is too large to display as seen below...

[ATTACH=CONFIG]246344[/ATTACH]

Opening them with "Document Viewer" just provided me with an endless rotating loading icon and "GIMP" eventually froze my computer.  After waiting several minutes I gave up on those and tried "Shotwell Photo Viewer".  Shotwell opened without error or endless loading icon, but only displays blackness as shown below...
 
[ATTACH=CONFIG]246343[/ATTACH] 

Is there another image viewer I should try, or could this be an issue with my hardware?  I'm running a Pentium4 2.7GHz with 2G of RAM (not a powerhouse, but I think adequate enough to open a 13.2MB picture file).

---

### Post by The Spectre on 2013-09-19
Try using Firefox or Chrome to view the .tif file.

If that .tif file is Compressed it could actually be much larger than 13.2 MB in size.

Typically .tif uses Lossless Compression but it can still have a big impact on the file size, especially if that file has very little detail (Like a log file that is all text).

Since you can open it on your Windows machine try saving it in a .BMP format to see what the true uncompressed file size is.

---

### Post by Petro Dawg on 2013-09-19
Thanks for the suggestions.  I tried opening with browsers and the image only downloads or asks to open in another program, I can not figure out how to get it to actually display in the browser window.

I saved the file as a JPEG file on a Windows machine, I will try to open it in that format when I get home.  It seems I underestimated the size of the picture a bit; it appears to be 3600 x 256570 pixels.

I'm not optimistic about being to open it as a JPEG either since the machine with a COREi7 and 8GIG RAM appears to get bogged down and takes several minutes to open.

The file size does not appear to change when saved as a BMP, JPG, or TIFF.    I think I will just take screen shots of the areas I'm interested in, and deal with having multiple small picture files instead of these huge monsters.

I had no idea viewing static images was this resource intensive.

---

### Post by The Spectre on 2013-09-19
Chances are that it will choke on the JPEG also.

Instead of taking screen shots of just certain parts why not try changing the resolution of the .tif file and save a copy of it to use on you Ubuntu machine?

---

