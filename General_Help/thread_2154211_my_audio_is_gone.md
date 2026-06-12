---
title: "my audio is gone"
date: 2013-06-13
forum: General Help
---

### Post by ELMIT on 2013-06-13
since the last update, my audio is gone!

I tried different programs that would use audio, like skype, Youtube ... no sound anymore

Checking Volume control / output devices I see  Port HDMI   - but I have no device on my HDMI port.

How can I track down this problem?

---

### Post by CatKiller on 2013-06-14
You could try to track down why your other hardware isn't being picked up by Pulse. PulseAudio uses ALSA as its backend to actually communicate with the hardware, so that's a good place to start.

---

### Post by ELMIT on 2013-06-14
Thats a great idea, .. and how do I do that?

---

### Post by CatKiller on 2013-06-14
A search for the name of your sound device + ALSA would be a start, since you think that it's a recent change.

---

### Post by sum1nil on 2013-06-14
I am not sure if this is what you are looking for but I have had numerous problems with sound with my little soundblaster (CA0106) sice Precise. It does take some tinkering.

To start I put on a video or mp3 to have sound going for a while, then type 'sudo alsamixer'.
Hit 'F4' to see what you inputs and outputs are currently, I've had to play with them to no end to get working sound.
While alsamixer is open also have open the 'pulse audio mixer' (gotten from the software center) and try different configurations, mine is '5.1 analog out + analog in'.
When you finally get some white noise turn down the output levels until you can hear the audio plainly. 

I wish I could be more help, but since 12.04 I have a terrible time with audio and still can not get skype going.

Best of luck.

---

### Post by ELMIT on 2013-06-17
just when I wanted to follow your suggestion, the sound came back. Strange!

---

