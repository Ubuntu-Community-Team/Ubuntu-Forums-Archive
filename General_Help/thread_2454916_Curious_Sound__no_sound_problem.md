---
title: "Curious Sound / no sound problem"
date: 2020-12-08
forum: General Help
---

### Post by michael351 on 2020-12-08
I have a desktop HTPC desktop (Intel I7-4790k) running Ubuntu 18.04 with an NVidia gt-1030 graphics card. Overall performance is terrific for movies and music when working.
This desktop is connected via HDMI to an AV 9.2 receiver for my home theater and connected to my home network.

I routinely access this desktop via XRDP from my home office computer for maintenance and loading media files.

If I boot my HTPC to play movies or music, the computer boots fine and loads the default gnome desktop where I run Kodi and other media applications.
The Nvidia card shows up in my sound sources as expected.

If, however, I XRDP to the HTPC desktop first (running XFCE desktop) from my home office and then start up the AV-processor/projector, the sound is missing - no sound card is listed at all, just dummy output. Not even pulseaudio is available.

Only if I reboot will the audio initialize and work normally.

I am just puzzled at what may be going and if there is a way to discover/start the Nvidia audio without having to reboot. It doesn't show up as a device.

---

