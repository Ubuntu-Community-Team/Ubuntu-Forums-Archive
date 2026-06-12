---
title: "Audio Recording Headaches."
date: 2008-02-29
forum: General Help
---

### Post by Omnistegan on 2008-02-29
Hey guys,

I seem to be having a bit of trouble getting audio capture to work properly in Ubuntu. Quick note on soundcards:

Asus P5N32-E SLI Motherboard with bundled soundcard. (SupremeFX (ADI 1988b))
Soundblaster Audigy soundcard.

Alright, so before I installed Ubuntu I was using the Soundblaster Audigy card with no trouble under windows. When I moved over to linux the Soundblaster card did not work, but the bundled Asus one did, so I've been using it. Audio plays fine, no troubles in any application so far.

I've been running my audio with all available channels turned on and up. Since encountering problems I've been able to conclude that my regular audio requires that I have "PCM" and "Front" turned up and on. I've also concluded that my microphone is in fact "Microphone". If I have both "Microphone" and "Analog Mix" turned up and on I can hear my mic through my speakers.

In a program like Audacity I have the following options for input devices:

OSS: /dev/dsp (runs, nothing records)
OSS: /dev/dsp1 (runs, nothing records)
OSS: /dev/dsp2 (does not run, check input settings)
ALSA: HDANVidia: AD198x Analog (hw:0,0) (runs, but very very slowly, and I'm on a Quad Core, nothing records)
ALSA: Audigy 1 [SB0090]: ADC Capture/Standard PCM Playback (hw: 1,0) (runs, then freezes Audacity, nothing records)
ALSA: Audigy 1 [SB0090]: Mic Capture (hw: 1,1) (does not run, check input settings)
ALSA: Audigy 1 [SB0090]: Multichannel Capture/PT Playback (hw: 1,2) (does not run, check input settings)
ALSA: USBDevice 0x46d:0x8da: USB Audio (hw: 2,0) (does not run, check input settings. This I find odd considering this Mic actually does work in Amsn)
ALSA: Default (runs, nothing records)

I'm really not sure where to go from here. It seems odd to me that I can get it to play my mic through my speakers but I can't manage to get it to record my microphone any which way. Any suggestions appreciated. Thanks for your time.

---

