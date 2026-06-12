---
title: "Very poor mic sound quality on Ubuntu 12.04"
date: 2012-11-17
forum: General Help
---

### Post by SuaSwe on 2012-11-17
Hi all,

I'm having some problems with my microphone on 12.04, specifically that the sound quality I get from it is extremely poor, to the point of being almost totally inaudible. I have tested it on GTalk and Skype with the same result, so it doesn't seem to be related to the application used.

I've had a look around the net for tips on what to do but have found surprisingly little to try; I'm also not able to figure out what soundcard I have installed. I'm on an Acer Timeline X laptop. From what I can tell, the laptop uses Conexant CX20588 codecs for sound.

I would be very grateful if someone could help point me in the right direction. :)

Cheers!

SuaSwe

---

### Post by SuaSwe on 2012-11-18
Bump?

---

### Post by NBPX on 2012-11-18
Same problem. Can listen my voice on sound recorder but with  noise.


Works in windows. Not a hardware problem, I think.


Acer Aspire. Ubuntu 12.10.

---

### Post by apochry on 2012-11-18
Hello,

launch "PulseAudio Volume Control" and go to the "Input Devices" tab. There play with the settings available. On my notebook the "Internal Microphone" setting causes noise problems, while the other ("Microphone") works fine.

[IMG]http://i.imgur.com/EoKJA.png[/IMG]

Note also, that Skype has a setting for automatic mic input volume adjustment, which I find not to work very well. So you might want to try disabling it and setting the mic input to the right volume manually.

If you don't have PulseAudio search for "PulseAudio Volume Control" in the SoftwareCenter.


Hope that helps!

   - Christo

---

### Post by NBPX on 2012-11-18
Still noisy...

:(

---

### Post by SuaSwe on 2012-11-19
Using Microphone instead of Internal Microphone results in complete silence for me, regardless of slider settings. :(

---

### Post by SuaSwe on 2012-11-19
Right, I've managed to get mine to at least audible quality by messing about with AlsaMixer, or more specifically by going to Terminal, typing in alsamixer, hitting F4, and configuring the mic settings as you see in the attached screenshot. 

Quality is still not brilliant but like I say, at least it is now clear enough to be comprehensible. :)

---

