---
title: "shotwell doesn't see my canon camera"
date: 2012-11-17
forum: General Help
---

### Post by Acharn on 2012-11-17
I don't use my camera much. I'm pretty sure I didn't connect it to my computer since I got my new hard drive and reinstalled Ubuntu back in August. So there have been a couple of birthday parties since then and a school event or two and I thought it would be a good idea to copy the pictures to my hard drive and then back them up to Ubuntu One. So I got out the cable and plugged in to the USB port and instead of a question about do I want to import my pictures I get a query, what software do I want to run. Funny, that never happened before. So I select Shotwell, because that sounds vaguely familiar and I don't remember what I was using before, F-Spot maybe? So Shotwell starts up and it doesn't see my camera. This doesn't seem to be a general problem. I can't find anything on Google or the forums about other people having trouble with this. What should I do next?

---

### Post by GreatDanton on 2012-11-17
I never had any problems with Shotwell, so I don't really know what may be the problem. I was able to import pictures no matter which camera I plugged in.

If you happen to have card reader I would transfer the pictures that way.

---

### Post by Peter Maunder on 2012-11-17
If it is the first time you have used Shotwell, you may find the help useful  HELP > CONTENTS or just press F1. This contains a good source of useful advice.

I would also check your preferences  EDIT > PREFERENCES to check which folders you are using for the photo library, date format, and storing the photograph meta data.

Your camera should show up as MASS STORAGE CAMERA on the top left hand side. If not for any particular reason you can import the photos by selecting FILE > IMPORT FROM FOLDER and selecting the storage card on the camera. It will normally show up as xx MB memory card.  DO NOT select the ERASE IMAGE AFTER COPYING as you will lose the original copy on the camera / card. 

If you can plug the card directly into your computer, as suggested above, that is a very good alternative.

---

### Post by eric-yorba on 2012-11-19
A couple of thoughts:

1. Shotwell sometimes won't see cameras that have been mounted by other applications.  Open your file manager and see if the camera is listed.  If there's an eject button next to it, click that and then restart Shotwell.

2. Try a different USB port.  Not entirely sure why this works, but there seems to be a Linux driver bug on certain machines and a number of users have reported this solution.

---

### Post by Acharn on 2012-12-23
Discovered 'gphoto2' wasn't installed. Surprised. If shotwell needs to use gphoto2, why isn't it one of shotwell's dependencies like it (apparently) used to me. Anyway, after I installed gphoto2, shotwell recognized my camera and I was able to download the photos.

---

