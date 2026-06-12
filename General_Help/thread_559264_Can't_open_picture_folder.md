---
title: "Can't open picture folder"
date: 2007-09-24
forum: General Help
---

### Post by HelloKitty on 2007-09-24
I have a Canon Powershot S3 IS.  It uses an SD card to store its files.  I'm on an Acer C200 Travelemate laptop, and although it has a built in card reader, it doesn't work (but for the most part, I'm fine with this).

When I plug in the Camera, it is immediately detected by Ubuntu (7.04).  I can browse the root folders, but when I try to go to the actual folder where the images are held, I get the error:

"Could not read file Fixed limit exceeded"

If I try to copy that direct folder, I get that same error.  If I try to copy a folder above it (while including it), the folder is 100% empty.  DigiKam, when it tries to bring the images over also gets an error.  That error is:

"Failed to list files in /store_000100001/DCIM/100CANON"  The folder, 100CANON, is the folder in question.


I have a Windows Computer, which can read the SD card (and through the camera).  I know there are a *lot* of images (approx. 1,000), I just don't know how to up the maximum files.

---

### Post by jsandys on 2007-10-18
I get the same error with my Canon A570 IS with the 2gig SD card.
Photo import works fine with a 1gig SD card in the camera.
And photo import works when the 2gig SD card is in a USB card reader.
UbuntuStudio with F-Spot, gThumb, gtkam, gphoto2.
I had to edit 45-libgphoto2.rules to get camera detection to work.

---

