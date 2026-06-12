---
title: "Soundcore Life P2 mic not working"
date: 2020-04-27
forum: General Help
---

### Post by iamtheliquor on 2020-04-27
Hi all,

I have a Soundcore Life P2 bluetooth headset;

[https://www.soundcore.com/uk/products/variant/life-p2/A3919011](https://www.soundcore.com/uk/products/variant/life-p2/A3919011)

Paired easy enough and the headphones work for audio with no issue, but I can't get the mic to work. Doesn't show up as a device in the sound settings;

[ATTACH=CONFIG]285641[/ATTACH]

I do see two devices in the Bluetooth menu, I have tried removing both and having either one active but it doesn't make any difference.

[ATTACH=CONFIG]285642[/ATTACH]

Was running 18.04 and had this issue, recently upgraded to 20.04, fully updated, same thing. Works with other devices, just not my laptop with Ubuntu on.

Any thoughts?

---

### Post by CelticWarrior on 2020-04-27
You need to change the default A2DP to HFP in the Configuration dropdown menu.
Be aware of the difference between this profiles:

[LIST]
[*]A2DP - HiFi Stereo audio, no Microphone -> Multimedia
[*]HFP ("Hands Fee") - Mono audio + Microphone -> Voice chat usage ONLY!
[/LIST]

---

### Post by nxdcalap on 2020-05-28
I'm thinking in buying this headset, I have Ubuntu 20.04 and I want to use them with Zoom. Did you finally fixed the Mic with what CelticWarrior said? 
Thanks!

---

