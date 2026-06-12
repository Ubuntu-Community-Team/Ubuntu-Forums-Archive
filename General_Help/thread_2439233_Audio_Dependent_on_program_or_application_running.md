---
title: "Audio Dependent on program or application running"
date: 2020-03-24
forum: General Help
---

### Post by gawardnz on 2020-03-24
Hi,
I have a Jabra headset that I use on my desktop machine running Ubuntu 18.04. This is a problem that uniquely affects the Jabra headset, but does not have any impact on my computer speakers that operate from the conventional analogue audio output. I am using the Jabra Bluetooth dongle as I have had an unrelated problem before when using the motherboards built in Bluetooth (insufficient volume).

My problem is that the audio is just fine (for example playing a Youtube video in my browser) however when I start up another application (only 2 applications do this to date, IE Telegram and OBS) the audio changes. The volume goes down slightly and the tone changes, it even sounds like there's a bit of echo too. My Jabra headset also announces "Mute" as I start the programs Telegram or OBS, but it does not actually mute, it just softens the audio level and corrupts it as explained.

I have Pulse Audio installed, and I've been through the individual audio settings, but the only thing I can find is audio settings for volume control, no tone controls on a per application basis. I've also looked in the audio settings for Ubuntu, but again, nothing in there seems to create (or eliminate) the audio effects I am hearing.

At this point I am at a bit of a loss, because I don't know whether this is a Jabra headphone driver issue, some other audio settings problem or Ubuntu itself. Any assistance would be appreciated, thank you, as I am meant to be getting setup to provide online training to my students now that we are all home bound thanks to the Corona Virus scare.

---

### Post by Yellow Pasque on 2020-03-25
Maybe alsamixer will be of more help controlling the volumes:
```
alsamixer
```
Pulseaudio has this "flat volume" setting that I don't care for. I don't know if that has anything to do with this or not.

---

