---
title: "Using Pipewire to Manage Calls on iPhone"
date: 2022-06-18
forum: General Help
---

### Post by Spiralagnus on 2022-06-18
I have PipeWire 0.3.48 as my default audio on Ubuntu 22.04. When I  connect both my headphones and iPhone 8 to the computer via Bluetooth, I  can stream audio from my iPhone to my headphones. However, I am unable  to make calls through my headphones. When I try to place an outgoing  call, the audio of that call still comes through the iPhone itself, not  my headphones.


 Changing the audio profile of the headphones doesn't work. For the  A2DP profile on my headphones, my choices of codec are SBC and SBC-XQ.  For HSP/HFP, my choices are mSBC and CVSD. I've tried all four  combinations, and in all cases, the audio for an outgoing call is still  coming through the iPhone, not my headphones. The iPhone itself only has  one audio profile: Audio Gateway (A2DP Source & HSP/HFP AG).


 Is there a way to use my headphones and PipeWire to make (and  receive) calls on my iPhone? This would allow me to listen to music on  my laptop and handle calls on my phone at the same time.

---

### Post by yancek on 2022-06-19
Looking at the Pipewire page, I see nothing there that would indicate it can be done.  Apple is extremely proprietary so it is always difficult to get their products to work with Linux.  Also, iphones are a small percentage of the world wide market so not much incentive for developer.

You might look at the page below which discusses the VLC for ios app which you can install on your iphone.  I see the following on that page:

>  Integration for bluetooth headsets and AirPlay including spatial audio for AirPods Pro and Max.i

I expect this would be quite a challenge if it is possible at all.  Good luck.

---

### Post by #&amp;thj^% on 2022-06-19
> **Spiralagnus said:**
> 
 Is there a way to use my headphones and PipeWire to make (and  receive) calls on my iPhone? This would allow me to listen to music on  my laptop and handle calls on my phone at the same time.

if your not the same poster as found on gitlab, you may want to join in: [https://gitlab.freedesktop.org/pipewire/pipewire/-/issues/2463](https://gitlab.freedesktop.org/pipewire/pipewire/-/issues/2463)

I have found with "Android",  If I want to use the headphones with the phone then it must be paired with the phone, not the computer

---

