---
title: "Problem with audio on Ubuntu 19.04"
date: 2019-07-29
forum: General Help
---

### Post by matthmit on 2019-07-29
So,i've installed ubuntu a few days ago in dual boot with windows 10,and since then every time i log in the sound is muted and i need to open alsamixer and disable auto-mute,just to turn my pc off/on and find that the auto mute is enabled again.

Removing and installing Alsa didn't worked,also sometimes a buzzing sound shows up when i'm listening to music and i need to turn off the PC to stop.

I had the same problem with ubuntu mate,right now i'm on W10 which is a much older installation than ubuntu and i have no problems with the audio,so i don't think the buzzing sounds are hardware problem.  
 
My mobo uses alc1220 codec,anyone know what i can do to try to fix this ?

---

### Post by matthmit on 2019-07-29
The mute problem was solved by typing **sudo alsactl store** on terminal,now i'm trying to fix the buzzing sound...after a few minutes listening to music on spotify it starts to make a really weird noise and only stops when there's no sound being reproduced...videos and sounds from the web has the same problem.

---

