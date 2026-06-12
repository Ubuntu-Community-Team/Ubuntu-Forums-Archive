---
title: "no midi,wi-fi + screen res probs"
date: 2007-11-22
forum: General Help
---

### Post by finlandrocks on 2007-11-22
I have a Mesh Ultima laptop 3.4ghz P4,17" tft ,Go Geforce 7800 mobile gfx card, Linksys Wi-Fi card and i think a Realtek sound card built into my laptop.

First prob is Ubuntu (Gusty Gibbon) wont recognize my Wi-Fi card and i cant find any suitable drivers, Any help please! Also if i were to go buy a USB Wi-Fi key which brand/model is guaranteed to work with Ubuntu?

Second prob ( more an irritation!) i cant get Ubuntu to go higher than 1024*786, my laptop is capable of 1600*1200 screen resolution, Any ideas?

Third prob is sound works fine (audio,mp3 etc...) but Midi files play silent with no sound, Help please ! I'm a musician with a Midi deaf laptop! Lol.

Many Thanks.

---

### Post by renzokuken on 2007-11-22
_1. wifi_

post the output of ```
lsusb
``` so we can find out what chipset you have

_2. resolution_
you probably need to install the nvidia drivers. this can be done with the "restricted driver manager" found in the System menu

_3. audio_
open a terminal and run ```
alsamixer
``` and play with the levels and make sure nothing relevant is muted

---

### Post by TidusBlade on 2007-11-22
I have totally no experience in Wi-Fi but I would suggest asking in the [Networking and Wireless Forum](http://ubuntuforums.org/forumdisplay.php?f=136).
As for screen resolution, try installing the Nvidia restricted driver through the restricted driver manager or something like that found in System > Admin (I forgot but something similar to that).
For the MIDI problem, I dont think it helps with midi, but try installing the package called "ubuntu-restricted-extras" from either the repos, synaptic or apt-get.
Hope it helps ;)

---

### Post by finlandrocks on 2007-11-29
sorry for late reply!
i have the nvidia restricted driver in use but still still with small resolution, heres that output you requested:~

Bus 005 Device 009: ID 0402:5603 ALi Corp. USB 2.0 Q-tec Webcam 300
Bus 005 Device 004: ID 07c4:a600 Datafab Systems, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 002: ID 0db0:6855 Micro Star International
Bus 004 Device 001: ID 0000:000

also i have run alsamixer and found nothing thats muted that shouldnt,still no midi playback sound.

---

