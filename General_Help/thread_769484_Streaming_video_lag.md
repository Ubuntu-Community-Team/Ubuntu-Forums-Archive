---
title: "Streaming video lag"
date: 2008-04-26
forum: General Help
---

### Post by cronohl on 2008-04-26
When ever i watch streaming videos on youtube or veoh i get this choppy video lag

im running hardy and i have flash 9 installed

---

### Post by Toxicity999 on 2008-04-26
If it isn't a simple networking issue, flash for linux still sucks, and it's something we have to deal with for now.

For a test case, try other browsers, opera, konqueror, etc. Further, do you have any networking issues to speak of? Or likewise any issues playing back basic video in totem, vlc, or mplayer?

---

### Post by cronohl on 2008-04-27
it doesn't have any playback problems i believe i tested it with 2 videos

i tried to download opera but i cant seem to get flash 9 on it
when o try to install flash 9 again it points me to /.Mozilla 

im not sure why it is not working because on the plugin sttings it says its detected the
plugin from firefox but when i go to youtube or adobeflash it dosent do the flash animations 

and im not sure if i have network problems i can surf and dl on the internet fine

---

### Post by Toxicity999 on 2008-04-27
It might just be an issue of flash itself being a pain. Flash for linux is still in heavy development, it's better than it used to be, but still not very good at all.

---

### Post by A$h X on 2008-04-28
Thing is though, flash/youtube/google video were all working FINE in gutsy, and now after an upgrade, they are all borked. I've tried re-installing the non-free plugin, still no joy. I've even tried using another browser (epiphany) and the problem perists, which leads me to believe it's a problem with hardy itself (or at least the crap plugin provided by adobe).
Anyway to find and install an old flash plugin?

---

### Post by A$h X on 2008-04-28
Well, I fixed the issue. For anyone who has the ridiculously choppy/stuttering video on youtube, google video etc. just go into synaptic and type "flash" into the search. Completely remove anything related to flash, EXCEPT ubuntu-restricted-extras, and restart firefox. Now your videos should play properly, no need to install any other plugins etc.

I know this shouldn't work, but hey it does and it's good enough for me. Hope it helps anyone else with this problem.

---

### Post by cronohl on 2008-04-30
it seems to be working fine right now maybe my connection was just alittle laggy that day 

and i didnt try your idea A$h and i wouldnt advice people to do that either just dosent sound logical

---

### Post by Ripfox on 2008-04-30
Why, restricted extras includes the non-free flash plugin. Essentially you are just removing and reinstalling it, which is logical enough I guess :)

---

### Post by Toxicity999 on 2008-05-02
It doesn't include it, it depends on it. Big difference.

---

### Post by Ripfox on 2008-05-03
Yes but you can install each component of the package seperately if you want so...whats the point.

---

### Post by PaulRay on 2008-11-11
Thank You! That did it for me. 
Running Intrepid on an older Alienware Laptop.

---

