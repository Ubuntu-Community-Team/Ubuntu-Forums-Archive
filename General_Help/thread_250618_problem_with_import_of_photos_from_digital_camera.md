---
title: "problem with import of photos from digital camera"
date: 2006-09-04
forum: General Help
---

### Post by Old Jimma on 2006-09-04
I upgraded to Dapper from Breezy and have the following problem importing photos from my Olympus C-4040.

When I plug my camera into the USB, Dapper sees the camera, mounts it, and puts a nice "hard disk" icon on my desktop.

When I open that icon to look at the photos on my camera, the photos I most recently took are not there! OLD photos that i had erased before my most recent shooting session are!!

WHen I unmount the camera, and then look at the photos (thru that monitor on the back of the camera) the new photos are there!

What should I do?

Thanks,
Phil Smith
Duluth, GA

---

### Post by meng on 2006-09-04
What if you hit Reload in the file browser, is the photo collection still outdated? (I find it easier to buy a USB card reader and use that rather than worry about camera compatibility, fortunately card readers are cheap.)

---

### Post by Old Jimma on 2006-09-04
Hi Meng:

Reload did not work.

:-(
Thanks,
Phil

---

### Post by Old Jimma on 2006-09-04
If you have trouble with Ubuntu not seeing the photos that you just with your camera, but sees photos that you erased with your camera... here is what worked for me:

1. go to another computer where you can download your new photos, then burn a cd of them to take to your computer.

2. DO NOT erase the photos with your camera software! (You will let Ubuntu do this in step 4, below.)

3. Connect your camera to your ubuntu machine, let it mount your camera. 

4. When it opens the folder with photos, MOVE ALL OF THEM TO TRASH.

I.E., let linux do the work of cleaning off your memory card, not the software on your camera. After your next shooting session, connect your camera to Ubuntu, let Ubuntu mount your machine. You will see all of your photos. Move them to the directory of your choice, THEN ON THE MOUNTED CAMERA DEVICE, MOVE ALL THE FILES TO TRASH.

Phil Smith
Duluth, GA

---

### Post by meng on 2006-09-04
Thanks for posting this. Although I wonder whether your card will eventually get cluttered with a whole bunch of files within the .Trash-phil (or whatever your username is) directory! Often with removable drives you should consider enabling the Nautilus option for deleting files and bypassing Trash altogether, you can then access this function by right-click menu or Shift-Del. Otherwise the files are just moved to a hidden directory on your removable media.

---

### Post by Old Jimma on 2006-09-04
Meng had a good point about the possibility of hidden files on my camera... 

As an experiment, I mounted my camera and used Nautilus to determine whether Ubuntu had put hidden files or folders on my camera after after moving everything from the camera to TRASH.

Nautilus showed no hidden files or folders.

Thanks to Meng for a good point! It may be that somebody who knows Linux better than I (that would be almost anybody) would know whether I overlooked someting here!

Best regards,
Phil Smith
Duluth, GA

---

### Post by meng on 2006-09-04
Well at least you know for sure now!

---

