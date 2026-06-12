---
title: "Auto load Canon camera drivers"
date: 2007-12-16
forum: General Help
---

### Post by Lord_Dicranius on 2007-12-16
Is there a way to auto-load the Canon camera drivers during login?  As of right now, it takes a good few minutes after plugging in a Canon Digital Rebel XT for the drivers to load before I'm able to transfer the pictures from the camera to a specified folder.  As my wife is into photography, I'd like to speed up this process a bit, and the only way I could think of was to have the driver load at login so when the camera is plugged in, we don't have to wait.

Any help with this, or another idea to speed up the process would be greatly appreciated.  Thanks in advance! :)

---

### Post by matthewcraig on 2007-12-16
Greetings, sorry you are having an issue with your Canon support.

Try editing the /etc/modules file.

This should make the support available when you plug in your camera.

---

### Post by Lord_Dicranius on 2007-12-16
The problem is I'm not sure which file to place in /etc/modules.  When the camera is plugged in, gThumb opens and starts to load the driver.  On the status bar, it says it's loading from from "/usr/lib/libgphoto2/2.4.0/..."  It doesn't tell exactly which file it's loading.  When looking in that directory, the only 2 files I see that it could be loading are "canon.la" and "canon.so".  I'm not sure what either of these files do, I'm not familiar with the file extension (a quick Google didn't bring up much either).  Checking the results of "lsmod" after the driver is finished loading didn't help either, I couldn't see anything to do with "canon".

---

### Post by Lord_Dicranius on 2007-12-18
Well, doing a little more research I found that the "canon.la" and "canon.so" files are part of libgphoto2, which gives other applications access to the camera.  Which is why gThumb is the application that loads when I click "import photos" after plugging the camera in.

I ended up caving and getting a flash card reader.  One thing that I found out that annoys me about CF cards, a bunch of chronologically numbered folders are created on the card, then the pictures are stored inside these folders.  And you have to go through each folder and copy/paste (or cut) the pictures to your desired location.  Anybody know a way around this (besides opening a file browser and going to the location)?  I like how when you plug the camera in, gThumb automatically finds the pictures on the camera and you just choose whichever ones you wanna import.

---

### Post by cbtengr on 2007-12-18
"One thing that I found out that annoys me about CF cards, a bunch of chronologically numbered folders are created on the card, then the pictures are stored inside these folders."

This is due to the way Canon sorts the files on the card, not a property of the CF card.  I have the same camera.  When used on Windows XP with the Canon EOS Utility, you can control how the folders are named (date, event, etc) when copied to the computer.  When done directly from the card with a card reader, you see the folders as the are stored on the card by the camera.  Canon places 100 shots into a folder, then creates a new folder and gives it the next number.  This continues until there have been 999 folders created.

I'm XP right now, I'll check Ubuntu on the other machine tomorrow.

GH

---

### Post by Lord_Dicranius on 2007-12-18
> **cbtengr said:**
> "One thing that I found out that annoys me about CF cards, a bunch of chronologically numbered folders are created on the card, then the pictures are stored inside these folders."

This is due to the way Canon sorts the files on the card, not a property of the CF card.  I have the same camera.  When used on Windows XP with the Canon EOS Utility, you can control how the folders are named (date, event, etc) when copied to the computer.  When done directly from the card with a card reader, you see the folders as the are stored on the card by the camera.  Canon places 100 shots into a folder, then creates a new folder and gives it the next number.  This continues until there have been 999 folders created.

I'm XP right now, I'll check Ubuntu on the other machine tomorrow.

GH

Ah, good to know.  Thanks for the info cbtengr :)

---

### Post by cbtengr on 2007-12-19
This is the first time I've connected this camera to Ubuntu machine.
Camera Detected window opened in less than 5 sec.
Import Photos window took about 10 sec to open, then read from card.
While this card has several folders on it, all images were displayed in the import window.  The only indication of different folders was in the image file name.

IM_1035-1099  (folder 10)
IM_1100-1125  (folder 11)

I don't know what is causing the long delay you're experiencing.  

GH

---

### Post by Lord_Dicranius on 2007-12-19
Thanks for looking into that cbtengr.  I'll look into it more when I get home, and hopefully report back with some good results *crossing fingers*

---

