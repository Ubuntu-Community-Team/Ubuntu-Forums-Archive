---
title: "No Sound - Used to have sound"
date: 2007-03-10
forum: General Help
---

### Post by samjaynes on 2007-03-10
I am hoping someone can lead me in the right direction...  My 6.10 install is about a month old, and I used to have sound.  I played some MP3s, and even got a DVD to playback (sort of).   However, the last week, I have had no sound what so ever.

lspci -v | grep audio
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)

sudo alsamixer shows the master volume at 58.  I doesn't appear to be muted, and I can adjust the volume control on the panel.  Still no sound.

Since I am fairly new to Linux, I am hoping someone can help.  Thanks..

---

### Post by rapidwiz on 2007-03-10
Run alsamixer from the command line, make sure is says 00 and not MM, use 'm' to turn your sound back on. If this doesn't work, search the forums for alsamixer for more info.

---

### Post by rocketman768 on 2007-03-10
Go back to alsamixer and check to see if there is a switch called "analog/digital" or something similar. Sometimes, this switch would get flipped to digital on my machine and no audio would come out of the speakers.

Otherwise, I'm not too sure. You sure you didn't install (or change) anything that could have altered your sound?

---

### Post by samjaynes on 2007-03-10
Thank you both for your replies... I went back into alsamixer, and found the issue.  Master was set correctly, and was active... the issue was that PCM was at zero.  Again, thank you for pointing back to alsamixer.

---

### Post by elykkyle on 2007-03-12
the exact same thing happened to me.  what's going on here?  I had to turn PCM back on as well...

---

