---
title: "[SOLVED] Audio/Video Distorted: Low pitch/slowdown (15.10 Intel NUC)"
date: 2016-02-20
forum: General Help
---

### Post by sailor420 on 2016-02-20
Hi all,

Seeing a strange problem on an Intel NUC box (NUC5i3RYH with a Broadwell i3 processor) running 15.10. Within the last day or so, all audio, whether from a video file, played from web (e.g. YouTube), or otherwise has been distorted, coming out at a low pitch that sounds like someone slowed down the audio. 

This is probably one of the stranger issues I've seen, and I'm not even sure where to start debugging it. Have spent last 30 minutes googling, and cant find anything that seems to be related.

Machine is, as noted, an Intel NUC running on 15.10. Audio and video are both output through HDMI.

This issue only appeared in the last 24 hours, so I have dumped a list of all the packages installed/updated in that time--was just standard apt-get upgrade type stuff, no other tinkering going on.

[https://paste.ubuntu.com/15152871/](https://paste.ubuntu.com/15152871/)

Any suggestions on how to start debugging this? Any help or pointers appreciated.

Update: Appears video as well as audio in slow-mo. Solution below.

---

### Post by sailor420 on 2016-02-21
As an update to this, I'm not sure that it's not all of the video playing in slow motion, along with the audio.

Any thoughts? I do see that some graphics drivers were updated recently through apt-get update.

---

### Post by sailor420 on 2016-02-21
So, as an update--it definitely seems to be related to the video drivers, specifically the Intel Graphics for Linux drivers from [https://01.org/linuxgraphics](https://01.org/linuxgraphics). I had installed these drivers from Intel several months ago to make sure I had the most up to date video drivers for the Broadwell graphics on the CPU. There was a new release of these drivers earlier this week that had been picked up in an apt-get update/upgrade.

I uninstalled these drivers by downgrading everything that had been installed from the Intel repos using the instructions from the link below (updated for 15.10). Once this happened, the problem went away. Not sure why, but I will mark this as solved and post a note on the Intel forums to see if anyone else is seeing this.

Intel Graphics for Linux Uninstall Instructions: [http://theclonker.de/archive/89](http://theclonker.de/archive/89)

---

