---
title: "Volunteers Needed (w/ HD on-board audio)"
date: 2008-04-24
forum: General Help
---

### Post by Yellow Pasque on 2008-04-24
The OpenSound System (OSS) project needs volunteers with general Linux knowledge to help build a High-Def mixer GUI. This is an alternative to the ALSA architecture supplied with Ubuntu.

> 
Hi all,

I have been working on a new hdaudio mixer driver that could create mixer/control panel interfaces that make perfect sense. The idea is to create lists of signal paths from input jacks to the ADC converters, from DAC converters to the output jacks and for (monitoring) paths between input and output jacks. If this can be done it should be relatively easy to show only the important controls in the mixer interface and to hardwire the unnecessary controls to sane values.

At this moment this hacking is done in a user land application. After it works I will implement the actual driver. An assumption I have made is that all current HDaudio based motherboards/laptops meet the Windows Vista logo compatibility requirements (UAA audio spec). To be able to verify how the pathing algorithm works I will need your help. If you have a PC/laptop with High Definition Audio then could you do the following:

- Pick the latest OSS 4.1 tarball (oss-v4.1-080423) or the oss version in the Mercurial server.
- Recompile and install it.
- Compile the mixgen2 program (cd utils;make mixgen2) and run it (./mixgen2).
- Send me the output of mixgen2 as well as the output produced by "ossinfo -d". I will also need the exact manufacturer/model of your PC/motherboard/laptop. Also tell if there is a "Windows Vista compatible" sticker on the system.

Please send the above info directly to me (hannu@opensound.com) instead to this forum. I will the change the mixgen2 program and ask for new info (if necessary).
[http://www.4front-tech.com/forum/viewtopic.php?t=2601](http://www.4front-tech.com/forum/viewtopic.php?t=2601)

---

### Post by Yellow Pasque on 2008-04-24
Anyone up for it? Please post and let me know if you do this, so I can tell if it was a good idea to try and recruit people here.

> In particular the systems that don't have any Vista sticker or that are older than Vista are interesting.

Btw, there is a bug in the mixgen2.c program of v4.1-080423 (fixed in the hg server). On line 1147 the device to be opened should be "/dev/oss/oss_hdaudio0/pcm0" instead of "/dev/oss/hdaudio0/pcm0".

Best regards,

Hannu

---

