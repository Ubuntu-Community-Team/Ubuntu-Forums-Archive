---
title: "How to Create Custom Icon?"
date: 2013-04-18
forum: General Help
---

### Post by Ubuntist on 2013-04-18
I have a 700-kB JPEG image that I'd like to use as a desktop icon for one of my folders.  I've already set the folder's icon to be the image, but this seems to cause Nautilus to sometimes go into an infinite loop, consuming a large amount of CPU in the process.

I'm guessing that what I should do is convert the JPEG file into a much smaller SVG file or a 48x48 PNG.  Is that right?  How would I do so?  Where is the best place to put the new icon once I've created it?

---

### Post by ibjsb4 on 2013-04-18
Nautilus-image-converter can reduce the size.  Its in the software center.

---

### Post by Thee on 2013-04-18
1. Open up the image in GIMP.
2. Choose Image > Scale Image, from the menu.
3. Enter the size you wish the icon to be and press Scale. Typical sizes are 32x32, 64x64, 48x48, 128x128.
4. Choose File > Export... and save it somewhere as PNG image.

There you go.

---

