---
title: "Sound Suddenly Stopped Working"
date: 2007-03-16
forum: General Help
---

### Post by palcal on 2007-03-16
My sound has stopped working today. I was listening to music before bed, so no problems. This morning when I decided to listen to some music, no sound whatsoever. I checked to make sure no one had used my computer, and they hadn't. I made sure that my speakers were all connected, sound wasn't muted, etc. My audio device is recognized, but when I tried to modprobe the driver (which I think is ICH7 for me) it couldn't find it. I have no idea what else to do and why my sound would *suddenly* stop working when no one has touched the computer.

I'd appreciate any help. I worship my music :guitar:

---

### Post by Pikestaff on 2007-03-16
What music player do you use, and do you get any error messages or anything when you try to play music?

---

### Post by palcal on 2007-03-16
> **Pikestaff said:**
> What music player do you use, and do you get any error messages or anything when you try to play music?

Tried the default music player, Totem and Amarok; no errror messages. When I tried to listen to an internet radio and YouTube I had no sound there either.

---

### Post by Pikestaff on 2007-03-16
Hmm, I have a similar problem where sound will suddenly quit working, usually after I've just watched a YouTube movie or something but I usually get an error message talking about xine or mp3 support, so I don't know if my problem is the same as yours.

For me, logging in and out or restarting the computer seems to fix the problem at least temporarily, so you might want to try that.  You may also want to take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=205449") which will help you to narrow down the problem... good luck!

---

### Post by isync on 2007-03-16
My sound too dies from time to time. Only a reboot helps- as I have not so far figured out how to warm-reset the sound-subsystem...

---

### Post by palcal on 2007-03-16
Removed and reinstalled packages as suggest but to no avail. I'll try the LiveCD and see if sound works that way. Then I guess I'll have to reinstall Ubuntu or something... which I'd rather not do.

---

### Post by palcal on 2007-03-16
I just tried the LiveCD and the greeting sound worked, so I assume sound is fine on the LiveCD, which means there's something wrong with my configuration? Is there a way I can have a fresh install without deleting my personal files (in /home which is on a separate partition)?

---

### Post by palcal on 2007-03-17
Fixed it at last! Funny solution, really. I opened up sound preferences and changed the device, which for some reason was muted. Switched it back to my default device, and it worked! Although, I could of sworn I had looked in sound preferences before and the other device wasn't muted...

---

### Post by Ambimom on 2007-03-17
It's the conflict between flashplayer and  the regular sound.......

For some reason, flash media content takes control of the sound....and won't relinquish control until you reboot... (Things like the videos on the New York Times page; some youtube videos but not all of them, etc.)

It was explained here in these forums by someone more technically literate than I....it's annoying but easily remedied...just reboot and your sound will return....

---

