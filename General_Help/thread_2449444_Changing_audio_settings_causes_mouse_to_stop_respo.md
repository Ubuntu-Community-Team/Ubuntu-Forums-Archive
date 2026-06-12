---
title: "Changing audio settings causes mouse to stop responding."
date: 2020-08-26
forum: General Help
---

### Post by chris-hancox on 2020-08-26
This is quite an unusual one.

I have a Raspberry Pi 4 running Ubuntu 20.04.1 aarch64 with Lubuntu desktop installed. For sound I am using a "CM106 like sound device" I purchased online. This is a 5.1 sound device.

When I have the sound device set to Analog Stereo Duplex, everything works fine through a pair of headphones other than my mic doesn't work (using a 3.5mm splitter, to split out the microphone to the red jack, as it is a "mobile phone" like headset with both Mic and Headphones on the one jack) but when I set Analog 5.1 sound + analog input, my mouse freezes. This does not matter what port the mouse is plugged into, and does not work with my touchpad remote control either. Unplugging the audio card restores control to the normal mouse. The only way to reset that I can tell is to delete .pulse in the home folder to make it forget the new setting and reboot.

I am guessing that the "Input" on the soundcard is somehow grabbing the mouse as it also does it when you select IEC958 optical input from the audio settings as well.

Can anyone please advise as to a fix, as I need to use my Mic for Duolingo and I can't use it at all currently.

---

