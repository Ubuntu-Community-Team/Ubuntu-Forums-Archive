---
title: "Spoof Phone Calls to Bluetooth Headset and Capture Audio"
date: 2019-11-02
forum: General Help
---

### Post by oohtuneboo on 2019-11-02
I use Ubuntu 16.04. I want to use my Bose Bluetooth earbuds as an audio capture device. I'm trying to accomplish this by making them believe there's an incoming phone call. So far I've been able to get them connected and playing music over A2DP with a combination of bluez and pulseaudio. I installed ofono and phonesim. So far, I've been able to get the HFP/HSP profile showing up as a sink via pacmd list-cards. When I set my default audio output sink to the headset and set the profile to be HSP, I can get the headset tricked into thinking there's an incoming phone call simply by playing audio to the headset. After that though, I'm unable to answer the call or to decline or anything. So I'm trying to figure out what I need to do with my desktop to make this work. From what I read, I think I may need to send some messages over dbus to set some properties and get the headset to think there's actually an incoming call. Then I guess I use parec to record from the headset source.

---

