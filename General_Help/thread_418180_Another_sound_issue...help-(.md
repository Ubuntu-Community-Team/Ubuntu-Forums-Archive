---
title: "Another sound issue...help:-("
date: 2007-04-22
forum: General Help
---

### Post by Psychomechanix on 2007-04-22
First of all greetings to all of ya!

I'm VERY new to Linux and I have to say, as someone who only knows Windows I am already impressed. There are alot of differences and Linux sure takes more effort but so far to me it is worth it. Completely fascinating. Looking forward to someday being knowledgable about the OS.

Problem: (Feisty Fawn 7.04 32bit just installed.) Sound sometimes works, sometimes doesn't. Sometimes rebooting fixes it, sometimes not.  

I noticed that Feisty detects 2 sound devices on my machine. One is my Soundblaster Live! card and the other is my onboard sound which is DISABLED in BIOS. 

If I do a "aplay -l" in terminal I get the following.

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I am assuming that "ca0106" is my soundblaster card and "via82xx" is my disabled onboard sound chipset.

Now for my questions:

1. Any idea why Feisty  sees multiple instances of each card? 
2. Is there any way I can get Feisty to forget about that disabled onboard via8xx card altogether?
3. I have read that in systems with multiple soundcards, ALSA randomly assigns one of them "default status" at EACH boot. This could explain why my sound works on some boot ups but not others. How do I get ALSA to recognize my soundblaster as default once and for all?

I have already made sure that everything is un-muted and turned up in AlsaMixer. I have also gone into System/Preferences/Sound and set everything to "ca0106". (It liests 4 different "ca0106" but the 4th one in the list seems to be the right selection and is the only one that gives me an audible tone when I click "test".)




Please keep in mind I am EXTREMELY new to Linux so if you have any instructions for me could you model them for a complete idiot. Thx :-)

My system info:

AMD 64 (1.9G)
Asus A8V motherboard w/onboard Realtek AC97(disabled) and onboard gigabit LAN
2G Corsair Ram
NVidia 6800GT AGP video
Soundblaster Live! PCI Soundcard

PC speakers and Microphone both 1/8" input jack style. No USB sound devices.

USB Gaming keyboard, PS2 Wireless Mouse, USB Joystick. 

OS: Ubuntu Feisty Fawn 7.04 (32bitx86)

---

### Post by GwydionThendon on 2007-04-22
Hi,
I had a similar problem and I managed to solve it with the guide found at this link
[http://www.linuxquestions.org/questions/showthread.php?t=499520]("http://www.linuxquestions.org/questions/showthread.php?t=499520")

Hope it is useful also for you,
Bye

---

