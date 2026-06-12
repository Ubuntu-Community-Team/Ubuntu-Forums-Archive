---
title: "Bluetooth/pulseaudio and handing over between devices"
date: 2021-10-10
forum: General Help
---

### Post by alecjw on 2021-10-10
I'm at my wits end trying to debug a bluetooth audio issue and I'm wondering if anyone would be able to help me please? It's to do with handover between devices.

I have a pair of bluetooth headphones (Bose Quietcomfort 35 II). These can be bluetooth-paired to two devices at once (eg phone and tablet). For audio playback, the expected behaviour is that audio can be heard from one device at a time. Pausing music on one device then playing music on the other should cause a seamless handover while both devices remain connected.

I have my headphones connected to both my phone (android) and my xubuntu PC (A2DP sink via pulseaudio). The problem I have is that when I have my laptop connected, my phone is completely muted. Even with no audio playing from my laptop, I can't hear anything from my phone.
The only remedies I've found are:
[LIST]
[*]manually disconnect my laptop whenever I want to hear something from my phone.
[*]or go into pavucontrol and change the bluetooth sink type from A2DP to none
[/LIST]
Both of these are inconvenient since I don't want to have to go fiddling in settings every time I want to pause a video on my laptop and go back to listening to music on my phone.

I think this is a problem with the behaviour of pulseaudio: I guess it presents itself as "playing music" (ie sinking via A2DP) all the time while the headphones are connected. Whereas the headphones perhaps expect the device to only sink over A2DP when it's playing something.

So my question is, is there any way I can configure this to realise the expected behaviour of the headphones (ie being able to hear audio from my laptop, pause it, then hear audio from my phone)?

I've tried enabling pulseaudio module module-suspend-on-idle but this just stops my bluetooth headphones from working at all. (edit: actually now i seem to have audio working with this module enabled, but i still have the same problem with no sound from my phone)

---

