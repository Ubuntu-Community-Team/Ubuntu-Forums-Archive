---
title: "[kubuntu] Stop Phonon from overriding pulseaudio output device"
date: 2018-01-07
forum: General Help
---

### Post by daniel-callejas-sevilla on 2018-01-07
Hi all,

Kubuntu 16.04.3 LTS here. My sound works very well under KDE very well, using PulseAudio as backend.

One minor but frustrating glitch I would like to solve: I usually listen to music albums with Amarok. When music starts to play, I open pavucontrol and adjust the output device to send sound to the proper device. Whichever is the proper device depends on what I'm doing today: headphones are plugged to the motherboard soundcard, loudspeakers are plugged to a dedicated PCI sound card, and home hi-fi in the living room is in remote via a DLNA sink.

However, when the first track is done and Amarok plays the second track, Phonon overrides the output device I have manually set, and directs output to whichever device has the highest priority in my Phonon settings. This is obviously the wrong device in &#8532; of the scenarios, so I have to go back to pavucontrol and set again the output device as desired. The setting seems to stick for the following tracks.

I am blaming Phonon for this annoyance, but it might be some other setting (on Amarok? on PulseAudio?).


What advice would you have for me?

---

