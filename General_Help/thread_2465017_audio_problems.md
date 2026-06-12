---
title: "audio problems"
date: 2021-07-19
forum: General Help
---

### Post by hmiersch on 2021-07-19
hi.  
i need to use a microphone for online chat. the problem is that the microphone on my old headset (2 3.5 mm plugs, tried in both the front and rear sockets) doesn't work. so i went and bought a new headset (USB plug), but that microphone doesn't work either. when i try to record audio from either microphone, all i get is noise. because the USB headset doesn't work either, i'm beginning to think that something is wrong with my system. maybe a missing driver? BTW, i can use either headset to listen to music and other audio, but the microphones don't work :-(  

ubuntu 20:04

---

### Post by Autodave on 2021-07-19
If it is a hardware problem, a USB audio device is rather inexpensive and most work very well.  I have one here and have no probs at all with it. 

[https://www.amazon.com/gp/product/B01N905VOY/ref=ppx_yo_dt_b_asin_title_o01_s00?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B01N905VOY/ref=ppx_yo_dt_b_asin_title_o01_s00?ie=UTF8&psc=1)     at Amazon for $13.99US.

---

### Post by TheFu on 2021-07-19
I've never had any issue with any USB microphone that I've used.  I have a Plantronics headset, a Logitech webcam+mic and a Samson GoMic. They all are just plug-in-use.

So, the first question is does Linux see any of those sources?  Microphone == **Source** in the pulse-audio world.
[Https://ubuntuforums.org/showthread.php?t=2462882&p=14040864#post14040864](Https://ubuntuforums.org/showthread.php?t=2462882&p=14040864#post14040864) has the commands to see.

I also bought a 3-pak of cheap lapel mics for $9. These use 3.5mm jacks.  According to everyone on my video calls, these sound better/clearer than the other mics.  It is probably the placement.

Using **pavucontrol** is key to getting the microphones and levels set correctly.
pacmd and pactl are useful for sharing text data here.

Most of the time, the problem is simply levels or muted.

---

### Post by him610 on 2021-07-19
For the past six years, I have been using a USB Plantronics Blackwire C310 headset without any issues. It is a good headset.
What theFu says about *pavucontrol* is true.

---

