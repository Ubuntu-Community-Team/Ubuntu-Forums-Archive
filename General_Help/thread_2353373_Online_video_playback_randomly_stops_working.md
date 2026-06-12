---
title: "Online video playback randomly stops working"
date: 2017-02-21
forum: General Help
---

### Post by Harpratap on 2017-02-21
I'm running UbuntuGnome 16.04.2 on Dell E7440 and randomly videos on youtube, vimeo and other streaming websites stop working which I have to fix by doing a reboot.
This issue is very recent and might have started about only 2-3 weeks ago. 
I use Chromium for HTML5 playback and Firefox if a website needs flashplayer. But both of them are unable to play a video on any streaming website until I reboot my laptop. All I see is the first frame of the video and it doesn't play, YouTube shows a small overlay saying *if playback doesn't begin shortly try restarting your device.*

---

### Post by 6-uiuntu-7 on 2017-04-24
Hi,
I've encountered the same problem on my Ubuntu 16.04. First I thought the onboard Intel graphics controller causes the issue. After several times looking into log files without knowing what’s going on I found a entry from bluetooth which sounded not too suspicious in the first place. 
In fact, it was. 
I'm using a bluetooth headset and after disconnecting the headset from my PC, restarting and reconnecting it, the Youtube Video went back to work without need to reboot the PC.
I don't remember the log file entry at the moment but if it happens again I will do another comment.

Best regards
Michael

---

