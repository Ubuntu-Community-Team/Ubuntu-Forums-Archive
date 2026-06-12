---
title: "Usb/midi keyboard"
date: 2006-12-16
forum: General Help
---

### Post by petok on 2006-12-16
Hi, I have [this]("http://www.woodbrass.com/images/woodbrass/CLAVIER+M+AUDIO+OXYGEN+49.JPG") 
 keyboard and I'd like to use it to play some simple songs first. I know my way around in Ubuntu, but I just do not understand these midi programs. I do not want to make songs etc. for now, just play some basic piano. The keyboard gets detected in some applications and ' lsusb ' gives:
Bus 001 Device 006: ID 0763:0196 Midiman 
although seq24 says it is the M-audio oxygen 49.
Does anyone know a simple program, like [this]("http://www.rempro.nl/lmk.htm")?

---

### Post by hamptone on 2007-01-04
I have a similar problem, my usb based m-audio oxygen-61 shows up as bus 002 Device 003: ID 0763:0197 Midiman and is also listed in the sound cards as snd_usb_audio
When I try to use it in LMMS or any other program it doesn't work automatically and I can't find anything on whether it's a driver problem, connection issue or if usb keyboards even work on linux. It works fine in windows but I'm anxious to take advantage of all the linux tools I've installed.

---

### Post by Blackmag+c on 2008-03-17
bump. I also wish to know before I make the switch to linux.:guitar:

---

### Post by DoctorMO on 2008-03-17
Make sure you don't need firmware in your device to make it work right, all the midisport stuff requires firmware to be used although the usb ids noted here aren't the same, perhaps installing alsa-firmware may help or you may have luck following the alsa guide here:

[http://alsa.opensrc.org/index.php/Usb-audio](http://alsa.opensrc.org/index.php/Usb-audio)

---

