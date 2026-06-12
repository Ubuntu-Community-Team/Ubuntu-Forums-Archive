---
title: "Static Audio Noise With Headphones"
date: 2015-09-03
forum: General Help
---

### Post by angrymoose on 2015-09-03
I have what can best be described as static and crackling noise produced when i plug in my headphones. This problem starts when the computer boots and continues as long as I have not muted the audio. If I open the audio options and click the test audio button and click the test left or right speaker test option the static and crackling disappears, but as soon as I attempt to listen to something the static and crackling reappears. 

I am running ubuntu 15.04, but the problem occurs on both 15.04 and 14.04 lts.

This problem does not occur on windows.

---

### Post by HermanAB on 2015-09-03
Turn the microphone level down.

---

### Post by Ignacio_Tiraboschi on 2015-09-03
It's probably hardware and not Ubuntu, I would check in another computer and see what happens!

---

### Post by angrymoose on 2015-09-04
> **HermanAB said:**
> Turn the microphone level down.Turned microphone down and muted it with no luck. I think its Ubuntu specific, but I will test debian & fedora.

I have tried changing 
load-module module-udev-detect
to
 load-module module-udev-detect tsched=0 


> **Ignacio_Tiraboschi said:**
> It's probably hardware and not Ubuntu, I would check in another computer and see what happens!As I stated earlier this problem only occurs with Ubuntu and not with windows so it most definitely is not a hardware issue.  As I currently dual boot I use my headphones daily on windows with zero issues what so ever, it seems to be a driver or settings issue in the default Ubuntu install. Further more as stated in my first post I can cause what ever is causing the static to totally disappear with a weird sound test loop until I attempt to use the audio device again.

---

### Post by HermanAB on 2015-09-04
Try running the alsa mixer aumix.

---

### Post by angrymoose on 2015-09-04
No dice there seems to be a nasty bug between pulse & the via audio chip that my laptop uses. I have dedicated more time to resolving this issue than its worth. I thank you for you'r assistance but I am just going to call it quits and stick with windows on my laptop.

---

### Post by howefield on 2015-09-04
Closed at request of the OP.

---

