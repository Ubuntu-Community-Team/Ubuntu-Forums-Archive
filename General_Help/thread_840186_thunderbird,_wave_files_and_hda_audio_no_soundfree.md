---
title: "thunderbird, wave files and hda audio no sound/freezing"
date: 2008-06-25
forum: General Help
---

### Post by wandalalakers on 2008-06-25
Basically my Acer motherboard works while my Asus motherboard with HDA audio doesn't.  Anyone with thunderbird and hda audio able to play a wave file when they have incoming email?  I've contacted Mozilla about this but I guess they are stumped.

When I import a wav file to be used to a new email message sound, thunderbird
locks up.  I've tried two different wave files.  I'm able to play these wave
files using Amarok so they wave files do work just not when trying to import
and play them using Thunderbird.


Reproducible: Always

Steps to Reproduce:
1.open thunderbird, edit, preferences, general
2.play a sound, use the following sound file
3. browse, open, play and thunderbird locks up
Actual Results:  
thunderbird locks up every time steps 1-3 are done

When sending myself an email to test and see if the sounds works, thunderbird causes the operating system to not respond.  I have to right click on the thunderbird program and terminate the session.

I tried using my sound file two ways using the kde control panel and I still don't get sound with incoming email.

I just tried on another pc with kubuntu 8.04 and thunderbird version 2.0.0.14 (20080505).  My secondary pc is able to play sound.  My primary pc has an Asus motherboard and an onboard sound card.  My secondary pc has an Acer motherboard and an onboard sound card.

When doing a aplay -l from terminal I get this about my audio:

Asus motherboard
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Acer motherboard
**** List of PLAYBACK Hardware Devices ****
card 0: V8233A [VIA 8233A], device 0: VIA 8233A [VIA 8233A]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Basically my Acer motherboard works while my Asus motherboard with HDA audio doesn't.  Anyone with thunderbird and hda audio able to play a wave file when they have incoming email?

---

