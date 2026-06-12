---
title: "Total lockup of system when using mencoder"
date: 2008-01-29
forum: General Help
---

### Post by sorceror on 2008-01-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67250](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67250) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've got a worrying problem. Ubuntu 7.10 with all available updates, Dual Athlon-MP system, 1GB RAM, dual 120GB IDE drives, Nvidia 5700LE w/nvidia driver.

Occasionally I'll use mencoder to transcode DVDs to DIVX AVIs for my Palm Treo 650. I was able to do this successfully with 7.06, but I don't think I've done so since I upgraded to 7.10. Last night, I tried to grab a chapter or two of a DVD and had the system totally lock up while running mencoder. Screen goes black, hard drive access light solid-on, even pushing the reset button on the front of the case did nothing. I had to literally turn off the power supply in back to restart. It happened several times, and only when running mencoder. The system has been stable for up to a few weeks in other respects, even when running games, both Linux-native and under Wine.

Nothing was recorded in the logs that I could find. If necessary, I might be able to hook up an old Palm as a serial console and see if there's any debug info available, but somehow I doubt it.

It seemed to happen a few seconds into the second mencoder pass. Here's the relevant lines from the script I use:
[FONT="Courier New"]
# Two-pass encoding, takes longer but produces best quality for a given bitrate
mencoder -dvd-device ${DVDDEV} dvd://${DVDTITLE} -aid ${AUDIOTRACK} -chapter ${CHAPTER} -ovc lavc -lavcopts vcodec=mpeg4:vpass=1:vbitrate=${VBITRATE} -ofps ${FPS} ${DIVX} -oac ${AUDIO} -vf scale=${SCALEW}:-2${CROP}${PULLUP} -o /dev/null

mencoder -dvd-device ${DVDDEV} dvd://${DVDTITLE} -aid ${AUDIOTRACK} -chapter ${CHAPTER} -ovc lavc -lavcopts vcodec=mpeg4:vpass=2:vbitrate=${VBITRATE} -ofps ${FPS} ${DIVX} -oac ${AUDIO} -vf scale=${SCALEW}:-2${CROP}${PULLUP} -o ${NEWNAME}[/FONT]

I tried it with an ISO image of the DVD first, then I tried reading the actual DVD from two different DVD drives (hdd and then hdb). DVDs themselves seem to play all right, without lockups. Anyone have any clue? Is there perhaps some weird SSE instruction that the 7.10 version of mencoder is using that my Athlons don't like?

The closest bug I could find is referenced, but I don't think this is the same problem. No syslog output, for one thing.

---

### Post by sorceror on 2008-02-20
Figured it out - it's hardware related. At least one CPU in my dual-CPU box is bad, any heavy CPU usage locks it up. The fans are spinning and the heatsinks aren't particularly dusty; it may have overheated once and now the damage has been done.

Guess I'll be looking for a new motherboard and such...

---

