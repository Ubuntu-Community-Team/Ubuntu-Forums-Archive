---
title: "no sound through hdmi"
date: 2012-11-19
forum: General Help
---

### Post by dodgeman4life on 2012-11-19
I have a barebone mini pc that i am trying to run ubuntu 12.1 on. i have sound through my 3.5mm jack when i plug my speakers to it but i have my system running hdmi to my tv. It shows the option in setting to choose hdmi but i have no sound coming through my tv. could it be a missing driver for my barebone?
Here is the specs for my barebone

General
Brand
Giada
Series
Cube Series
Model
CUBE-N3-D2OB
Color
Black

CPU Supported
CPU Type
Intel Atom 330 (1.6GHz, dual-core)

Chipset
North Bridge
NVIDIA ION

Memory Supported
Memory slot
200Pin SODIMM
Memory Type Supported
DDR2 800
Max Memory Supported
4GB

Storage
Serial ATA
1 x SATA 3.0Gb/s

Graphics
Onboard Video
NVIDIA ION graphics processor

Audio
Onboard Audio
Integrated

Communications
Max LAN Speed
10/100/1000Mbps

Extension Bays
2.5" Internal Bays
1

Front Panel Ports
Front USB
3 (2 @ front, 1 @ side)
Front Audio Ports
Stereo Audio-Out / MIC-IN
Card Reader
1 × Card Reader (SD/SDHC/MMC)

Back Panel Ports
HDMI
1
VGA
1 x DVI
Rear USB
2
Rear e-SATA Ports
1 x eSATA/USB combo
RJ45
1
Rear S/PDIF Out
1 x Optical output

Power Supply
Input
12V DC-IN

Physical SPEC
Dimensions
7.64" x 5.35" x 2.17"
Weight
1.7 lbs.

Features
Features
Support 1080P high-definition
- Featuring the NVIDIA ION graphic solution, Giada cube N3 supports 1080P high-definition movie. Geforce 9400 GPU and CUDA 16 cores technology improves video encoding by 10 times. Game, movie…… it helps to enjoy your life.

Ultra-slim
- The book-sized PC only takes up small part of your table. It is even smaller than 1/30 of the standard desktop. The weight is less then 1KG, you can even carry it anywhere.

For barebone, up to 4GB DDR2 RAM and 500G hard disk
- You can choose the memory (max 4GB DDR2 RAM) and hard disk (max 500G) as you like and enjoy the fun of DIY.

Premium Windows experience with Windows Vista and Windows 7

Memory Option: 1GB, 2GB or 4GB DDR2

Include 23W AC Adapter

---

### Post by papibe on 2012-11-19
Hi dodgeman4life. Welcome to the forums ):P

Have you installed the Nvidia proprietary driver?

If not, open 'Additional Drivers', install what is recommended there, and then restart your computer.

Let us know how it goes.
Regards.

---

### Post by dodgeman4life on 2012-11-20
yes i am. and still have no sound through hdmi

---

### Post by mike555 on 2012-11-20
maybe a bad cable ?   I have read about problems with some cables .

---

### Post by efflandt on 2012-11-20
A start would be to see if you see a bunch of NVidia devices when in a terminal you do (thing after -iA is number one)

```
aplay -L | grep -iA 1 nvidia
```But I have a 2.1 PC analog stereo system with subwoofer that sounds better than my HDTV speakers and have not done HDMI sound since Ubuntu 11.10.  So I don't know if it still takes a bit of trial and error with specific **aplay -D** commands to find out which of the devices listed by aplay -L is actually for HDMI audio.

Someone who has set up NVidia HDMI audio more recently may be able to help further.  It might involve editing something in /etc/pulse/default.pa to tell pulse which alsa hw: device it is.

---

### Post by dodgeman4life on 2012-11-22
dont think its a cable. because i had windows 7 on it before ubuntu and it worked just fine

---

### Post by dodgeman4life on 2012-11-22
i just tried aplay -L | grep -A 1 nvidia in terminal and nothing came up

---

### Post by Takanakathehacker on 2012-11-22
Had a similar problem on my bros laptop.

Possible fix...

Go to sound preferences, then hardware (as i recall), change the scroll-down "profile" list to hdmi out. 

Its under either hardware, or output, can't remember which. ;)

Sorry think i missed a bit in your original post, i take it you've already tried this :P

---

### Post by dodgeman4life on 2012-11-22
thanks guys for the help but i think i just fixed my problem! i went to alasmixer in terminal and all the way on the right had side. the S/PDF i think. it was muted and i unmuted it and my sound went to working. thanks for the help

---

### Post by Takanakathehacker on 2012-11-22
ah fair doos, makes sense, pulseaudio is the other/usual sound server, that allows "hmdi out" to be changeable through sound preferences.

I'd disabled pulseaudio myself because i do some occasional recording in audacity, and it seems to cause conflicts. 

Have they sacked off pulseaudio for the later installs of ubuntu? Or did you disable it manually dude?

---

### Post by dodgeman4life on 2012-11-24
i never touched it unless i did without realizing it. i do have one more prob now. i do have sound but when i go to sound settings and test it it only comes out of my right speaker. i dont hear anything from the left. is there a fader on here somewhere that im not seeing?

---

### Post by dodgeman4life on 2012-11-24
it must have dont it itself unless i did without realizing it. i do have one more prob though. now that i do have sound when i go to my sound options and test it i only have sound coming out of my right speaker and not my left

---

### Post by dodgeman4life on 2012-11-24
it must have done it on its own. i do have one more prob though. now that i do have sound when i go to my sound options to test it, it only comes out of my two right speakers now. nothing on the left. i have it running though hdmi to tv and then red and white audio cables to my stereo

---

