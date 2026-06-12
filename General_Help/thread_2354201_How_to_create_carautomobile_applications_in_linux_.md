---
title: "How to create car/automobile applications in linux or any other technology"
date: 2017-02-28
forum: General Help
---

### Post by kenneth20 on 2017-02-28
[COLOR=#242729][FONT=Arial]Does anybody know what type of "courses" or technologies should I take to learn how to program applications for vehicles?, What technologies to use, for example, Java or C or whatever?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]For example, I would like to know where would I program in the car if I want the car to start without the need of a physical "key", or start alarm if someone touches the window.[/FONT][/COLOR]

---

### Post by TheFu on 2017-03-02
Every vehicle manufacturer will do it differently.  You'll need to be a specific brand, and possibly, model, to get started.  I would start by watching hacker videos on youtube. Those are extremely enlightening.  For example when the Nissan Leaf hacks were shown, it was using a REST interface from centralized servers and any web-client could be used to activate the different features.  A web-client can be emulated in almost any language, but something like python, perl, ruby, would be the most popular.

if you are trying to do this on android tablets or smartphones, then you'll want to use Java (the Android version).  On a normal Linux distro, it really shouldn't matter which language you choose.  Python won't be a bad choice.

As for doing the things you specifically list - that would be completely dependent on whether the manufacturer decided to place sensors and actuators into those controls AND make those available through any API.  For example, I don't know of any alarm systems that are sensitive to touch - they are either proximity or need a little shaking to go off, IME.

---

### Post by dragonfly41 on 2017-03-02
Voice recognition is just one theme to research ...

[http://www.nuance.com/for-business/mobile-solutions/dragon-drive/index.htm](http://www.nuance.com/for-business/mobile-solutions/dragon-drive/index.htm)

[https://arstechnica.com/cars/2016/01/dragon-drive-is-the-best-car-voice-activation-system-weve-spoken-to/](https://arstechnica.com/cars/2016/01/dragon-drive-is-the-best-car-voice-activation-system-weve-spoken-to/)

Then there is the "Internet of things" to study related to automobiles.

---

### Post by TheFu on 2017-03-02
I've deployed Nuance servers before.  At the time, they were Windows only (wouldn't run on anyother OS) and fairly expensive.  We were supporting about 1K concurrent users at the time using enterprise telecom equipment to get all the channels into the servers.

If you don't care about privacy, it is possible to use google/amazon/siri as a voice interpreter - send WAV files and get back text.  Then a simple parser with {subject verb object} can be used.  

In the old days, we did that with procmail interfaces to control servers via email.  A buddy setup bank ATM scanner deployments using procmail - you know the type that accept check deposits and scan/OCR the checks immediately?

Today, lots of people are building voice controlled systems with Raspberry Pis.  [https://diyhacking.com/best-voice-recognition-software-for-raspberry-pi/](https://diyhacking.com/best-voice-recognition-software-for-raspberry-pi/)  I don't know of **any** solutions that are local, however.  They need internet and a voice-to-text service.

BTW, I worked for a subsidiary of Ford a few decades ago - nothing to do with land vehicle, however.

---

