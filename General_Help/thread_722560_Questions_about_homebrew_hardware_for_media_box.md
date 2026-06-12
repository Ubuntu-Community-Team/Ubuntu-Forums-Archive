---
title: "Questions about homebrew hardware for media box"
date: 2008-03-12
forum: General Help
---

### Post by madsporkmurderer on 2008-03-12
Firstly, I couldn't really see an appropriate place to post this so mods feel free to move as necessary.

Basically I have pretty much build a media box, mainly for music but will probably see a little bit of video use (and I'm gonna leave things like firefox on there for those random conversations that lead to needing to look something up); I want a couple of extra hardware features that could probably be bought if I had the money, but I like tinkering so would like to do it myself just to learn how as much as anything else.

The first thing is a final stage amplifier, it will be driving at least 4 fairly hefty speakers and the standard onboard sound output is not up to the job; I was thinking of a dual power-op-amp based circuit, one op-amp per channel (stereo) and maybe have a variable resistor mounted on the front to adjust the gain of this stage, or just have a fixed gain and just use the software volume control. Does anyone know if soundcard outputs follow any particular standard or what voltage/current there is likely to be coming out?

The other thing that would be nice would be some front panel buttons that I could tie to amarok global shortcuts for things like play, pause, skip track, maybe volume up/down. This is an area I have no real knowledge of, I have been told that interfacing with the parallel port is the easiest way to have simple custom hardware but don't know how to go about it. I can cope with switches with pull up/down resistors, debounced as necessary but haven't really got a clue where to go from there. Once hardware is done I will, I assume, still need to do something in software; I am thinking I am going to have to add something to xorg.conf but don't know what, will I have to write my own drivers?

If anyone can answer any questions, make any suggestions, or provide any useful links it would be much appreciated

Thanks in anticipation,
Mike

---

### Post by Suparious on 2008-03-13
Computer audio output can be classified the same as a portable MP3/CD/Tape Radio, ect..

something like:

1Vrms into 10K load, upto 1.5W per channel into a 4 or 8W load. ([source]("http://209.85.173.104/search?q=cache:2o0fno0JjREJ:www.altistechnology.com/images/ACT/8043-cc_Spec.pdf+3.5+mm+Stereo+Output+standard+voltage&hl=en&ct=clnk&cd=3&gl=ca&client=firefox-a"))

The front panel button will be difficult, I think. The XOrg modification would work for additional buttons on the keyboard, not sure how the front panel buttons would be interfaced at the hardware level as they have nothing todo with input devices on PS/2 or USB. 

Most likeley, like with laptops, you may need somehting for the kernel from the hardware manufacturer. Then again, it depends on how the buttons are being read by the hardware.

---

### Post by madsporkmurderer on 2008-03-13
Thanks for the audio specs, I spent quite a while searching but had come up with nothing useful.

As far as the front pannel buttons go, I will be the hardware manafacturer- I am thinking of buying some buttons and the other necessary components and mounting them myself. If it would work better there is no reason why I could not interface with usb (ps/2 could be an issue as there will already be a keyboard and mouse). I was already expecting to have to do a bit of coding in order to get this working, what language do hardware drivers for a 'new type of keyboard' have to be?

---

