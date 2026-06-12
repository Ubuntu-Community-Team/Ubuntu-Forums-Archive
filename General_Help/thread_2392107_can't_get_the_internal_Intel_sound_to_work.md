---
title: "can't get the internal Intel sound to work"
date: 2018-05-16
forum: General Help
---

### Post by zdteHnM on 2018-05-16
Hi,

OLD computer, 32 bits. Running lubuntu 18.4.
Everything works fine except no audio.
PulseAudio Volume Control, in the tab Configuration, says: No cards available for configuration.
I see the Dummy volume moving when I go to a youtube page.

There is a soundcard though. If I type:

lspci -nn | grep -i audio
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)


I've tried unsuccessfully: (Always logging out and logging in before trying again.)

- Uninstall and re-install both pulseaudio and alsa.

 sudo apt-get remove --purge alsa-base pulseaudio
 sudo apt-get install alsa-base pulseaudio

- adding this line to the alsa-base config file

options snd-hda-intel probe_mask=1 model=auto

- Play around with the alsa mixer to make sure the soundcard is selected and not muted. By the way, I can see the soundcard in the alsamixer.

And no luck, pulseaudio does not see it and I don't get any volume out of the browser... any clue?

Thanks,
Regards,
Hipo

---

### Post by zdteHnM on 2018-05-16
One thing to add... while alsamixer sees my card, if I type
aplay -l

I just get an empty list...

**** List of PLAYBACK Hardware Devices ****

And nothing here...


aplay -L
default
    Playback/recording through the PulseAudio sound server
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
surround21:CARD=Intel
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=Intel
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers

---

