---
title: "Error interpreting JPEG image file (Not a JPEG file: starts with 0xff 0xff)"
date: 2016-03-18
forum: General Help
---

### Post by jgw on 2016-03-18
I am having a problem with certain jpg files.  I discovered this when transferring the files to my computer.  I checked the files on my camera and it showed the same problems.  The error I get is the subject of this.  My camera is a coolpix S9700 and has a 32gb sd card in it (formatted by the camera).

Below you will see the results of file and exif.  I was able to transfer all the files to my computer but that didn't change anything.  I am now wondering if my camera needs attention or if I am using the wrong sd card, or all sorts of other things (one gets a bit paranoid when this occurs)  I also just noticed that the folder I have these in just lost about 900 photos (just disappeared for no reason).  I am getting a bit concerned about all of this.  Its particularly interesting in that I did transfer a subset of these to a flash drive and they were all just fine.  I also notice that others have had problems with jpg files in the past.

When I originally took these off my camera, and transferred them to my computer I was able to see every file.  Not only that but the thumbnails are also still out there and they too look fine.  This is all very strange.  I need to know if its my machine or my camera although, given the strange things my machine is doing it may be that.  I should also mention that I have tried this on two separate machines with the same results.

I used the file command to get:
~/Pictures$ file DSCN5604.jpg
DSCN5604.jpg: AIX core file fulldump 32-bit, \377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377 64-bit, \377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377

I did the same with another problem file and got, exactly, the same results.  There were also a couple of .mov files in with the jpg's  and when I tried to view those it froze up the machine.  

exif returns:
~/Pictures$ exif -x DSCN5604.jpg
'DSCN5604.jpg' is not readable or does not contain EXIF data!

---

### Post by QDR06VV9 on 2016-03-18
After you format using the camera to that, is there any errors?
I have gone through what you are now experiencing got tired of chasing different solutions and bought a new SD Card.(They are Cheap Now)
I was able to use [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec") to recover my pictures though.
I had a repair guy give some good information as described below.
Memory cards are FAT formatted. (Mine is a FAt 16) When a file is deleted in FAT, the space is marked as free, but there can still be hidden fragmentation and corruption. Formatting rewrites the allocation table to make sure the space is continuous and you don't have any file-system errors.

 And fragmentation on a FAT file system is more common when deletion is scattered. If you empty the filesystem with deletes then fragmentation isn't a concern. 

 **I use my computer to delete photos from the card after importing them**. I reformat the card using my computer.(Fat16) About 3 to 4 times a year.
 For me it is useful to not reset the camera's image counter that generates the file names for images on the card. This lets me add images to my photo gallery on my computer without file name collisions.
But Sorry for the information all around your problem at hand.

---

### Post by jgw on 2016-03-19
I found the program PhotoRec already installed and was able to go over the chip and recover all the photos.  It took it over an hour but there were almost 1000 photos.  Anyway, I got all my photos back.  I still have no real idea of what happened but I am going to be a LOT more attentive when I am formatting these things.

Thank you for the replies....................

---

### Post by jgw on 2016-03-21
One last on this one.  I have now heard back from Nikon and they replied:
My thoughts are the memory card you are using is incompatible with the camera. The camera is not compatible with MicoSD cards which utilize SD card adapters. I have included a link below to the compatible cards:

Answer Title: Approved Memory Cards - Coolpix S9600/ S9700
[https://support.nikonusa.com/app/answers/detail/a_id/19062](https://support.nikonusa.com/app/answers/detail/a_id/19062)

---

