---
title: "priority audio-video-input"
date: 2007-08-30
forum: General Help
---

### Post by Jeek Elemental on 2007-08-30
Ive been using ubuntu feisty for a couple months now, and its great.
Skips in audio and framerate still bother me tho.

Are there any methods I can use to have sound>video>human input>everything else as a priority list?
I dont care about system performance as a whole (ie Id rather have a constant 40 fps than 650 on average).

system is fully updated feisty amd64x2 4600 nvidia 8600 2GB ram sata hdd, usb input devices
nvidia drivers 100.14.11 compiled locally
alsa usb sound (a simple external 16bit 44100 DAC)

minor niggles but if someone can offer advice on how to fix, itd be nice :)
My gnu-fu is medium-strength, a hint on where to start should suffice.

---

### Post by 5-HT on 2007-08-30
Are you using the box for audio/video production? If so and xruns are a problem I'd recommend getting a fully-preemptable realtime kernel, and editing your /etc/security/limits.conf as per your needs . Ingo Molnar, a kernel dev, maintains a great realtime kernel patchset ([http://people.redhat.com/mingo/realtime-preempt](http://people.redhat.com/mingo/realtime-preempt)), . Also, for audio work, a low latency sound server (e.g., JACK) is a must have, and will also need to be setup properly for your system.

If it's just a casual use box that's skipping on playback, might be a driver issue. If not, renicing the apps you want priority for is an easy thing to do (check out 'renice).

cheers,

---

