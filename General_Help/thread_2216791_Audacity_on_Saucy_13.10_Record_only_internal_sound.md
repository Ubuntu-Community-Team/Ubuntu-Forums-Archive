---
title: "Audacity on Saucy 13.10: Record only internal sound"
date: 2014-04-13
forum: General Help
---

### Post by SteveL1990 on 2014-04-13
Hi folks. I have a somewhat bothersome issue with Audacity and I'm not sure what to do. 

 I have used it for a long time on both Windows and Ubuntu, to record sounds, etc. Here's the problem; I am trying to set up Audacity so it records sounds played on the PC but *not* from the outside(such as fans, and other environmental sounds). Unfortunately, I'm having a good bit trouble figuring out how to get this to work on my current computer, running Saucy 13.10; I managed to do this on a previous PC on both Windows and Ubuntu(Natty 11.04), but now I can't figure seem to figure it out.

Again, just to clarify, I want to find out how to record only internal sounds played on the computer and nothing from the **outside**.

---

### Post by woohoomoo2u on 2014-04-14
Try switching the input of the speakers to the mic, I'm not sure how to do this on ubuntu...

---

### Post by SteveL1990 on 2014-04-14
Yeah, I tried everything I could find for both input and output and nothing worked. Is there something I have to download or something?

---

### Post by SteveL1990 on 2014-04-15
Still need help, btw. I checked the official manual & the wiki but while recording computer sounds are mentioned, it doesn't mention how to get Audacity to only record those internal sounds.

---

### Post by SteveL1990 on 2014-04-18
> **SteveL1990 said:**
> Still need help, btw. I checked the official manual & the wiki but while recording computer sounds are mentioned, it doesn't mention how to get Audacity to only record those internal sounds.

Anyone out there? :(

---

### Post by tgalati4 on 2014-04-19
There are several sound frameworks used in Linux.  Bring up *alsamixer* in a terminal and play with the settings so that you recognize the name of the channel that the internal sounds are played on.  Pick that channel in *audacity*.

Some reading:  [http://manual.audacityteam.org/o/man/tutorial_recording_audio_playing_on_the_computer.html](http://manual.audacityteam.org/o/man/tutorial_recording_audio_playing_on_the_computer.html)

---

