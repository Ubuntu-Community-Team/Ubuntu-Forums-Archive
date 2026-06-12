---
title: "Jack in UbuntuStudio wont record mic/line in"
date: 2007-05-21
forum: General Help
---

### Post by DeathByGuitar on 2007-05-21
I have 2 computers running UbuntuStudio 7.04. One is my laptop, with some sort of Intel audio chipset, and the other is a computer i built with a CMedia AC'97 chipset. 

Anyways, when I first booted UbuntuStudio for the first time on my laptop, I started Jack from Jack Control, then opened Ardour. I tried recording a few things from the mic input, and much to my supprise, everything worked perfectly.

I was not as fortunate with my desktop. Upon starting Jack and Ardour, I tried to record a few things. It wouldnt pick up anything but absolute silence. It works fine with Audacity in Windows though...


So does anyone have any ideas? I know very little about Jack (or linux audio to begin with), so any help would be appreciated. Thanks

---

### Post by DeathByGuitar on 2007-05-22
bump

---

### Post by eric71 on 2007-05-22
The only thing I can suggest is to double click on the volume icon in the panel and check that the mic is set as the recording input (and not line in for instance), not muted, etc. Everything can be set right in Jack, but if the Alsa settings aren't correct, it won't work. AC97 controls usually allow the choice of line in or mic for recording. My laptop doesn't even have a line in, so if this is selected rather than the mic, I get nothing.

---

### Post by treblesix on 2007-05-24
I am having the same problems.

Using Total Recorder on Windows, I can record audio from the line in, but I can find no way of doing this in Ubuntu. Anyone got any ideas?
I am not sure what all this 'JACK' stuff is about either, which is probably where the problem lies. 
Any audio being pumped into the line in socket, comes out the speakers, but I cant record it.

---

### Post by heminder on 2008-03-23
i'm having the same problem in Ardour running on Fedora 8 with guitars through line-in...
i think the principle is the same: sound through speakers but nothing on record or the monitoring...
probably a JACK connection missing...
does anyone know how to connect it... ?

---

### Post by ucaka on 2008-06-03
I had the same issue and i fixed it like this!
First sorry for the bad english. :)
First you need to go to the volume controls! In Preferences you should check:
1. Mic Capture
2. Capture
----------
Now open JACK and click Connections
There you should connect System - Capture 1 and Capture 2 to the program you'll use to record the mic or something else. If you need to record something from Line in. Do the same but instead in Vol controls to add Mic Capture add Line-in capture. I hope i helped

---

