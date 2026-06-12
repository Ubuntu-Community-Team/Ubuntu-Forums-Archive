---
title: "Mounting and sound problems in Gutsy"
date: 2007-10-23
forum: General Help
---

### Post by pacienca on 2007-10-23
Since upgrading to Gutsy, I have strange behavior of the system. If I load with kernel 2.6.22.14, I get no sound. But I can mount my external drives!:)
Why I mention this?
Because if I load with kernel 2.6.20.16, which is the other option available at start, I have audio working perfectly, but I cannot mount any external discs!
Any ideas?
In Feisty everything worked OK.

---

### Post by dayvy on 2007-10-23
I recommend sticking with the 2.6.22-14 kernel as Gutsy is developed around that specific kernel. What kind of sound card do you have? Is the module loaded?

d.

---

### Post by pacienca on 2007-10-23
Well, I'm using Presario laptop, and according to Hardware Information, sound card is Intel 8281 CA/CAM AC'97 with  Intel 8281CA-ICH3 Alsa Playback device

---

### Post by Raptor Ramjet on 2007-10-24
I was going to start a new thread but my problem might be relevant to this one.

I have a system with on onboard VIA822 sound chip (which I don't wish to use) and an SBLive sound card (which I always wish to use).  Now under Feisty this all worked fine, i.e. I selected SBLive from the volume control and all was well.

Having upgraded to Gutsy it's now pot luck whether it works or not.  Sometimes the SBLive gets allocated as card(0) and the VIA822 gets allocated to card(1).  In this case I have sound as I want it.  However the other times the VIA822 get allocated to card(0), the SBLIve becomes card(1) and I simply cannot get any sound at all to appear from the outputs of the SBLive.

I know I could disable the onboard sound in the BIOS (when I remember I'll probably do this "for now") but sound is definitely not working properly for me in Gutsy.

It would also be nice if you could choose which soundcard to use from the "Menu" > "Preferences" > "Sound" applet as it's not clear whether choosing "Default Mixer Tracks" selects the soundcard to use or whether it simply determines which controls get shown in the volume controls mixer (I suspect the latter)

There definitely needs to be something in the sound dialogue where you can choose your default sound card !

Most annoying really.

---

