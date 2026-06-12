---
title: "HDMI sound flawless only when PulseAudio Volume Control is open?"
date: 2014-07-04
forum: General Help
---

### Post by neu5eeCh on 2014-07-04
So, it goes like this: As soon as I start up the "pulse audio volume control" dialog box, the sound (from youtube for example) is flawless. When I close the dialog box, the sound goes back to being a mess -- a sort of pulsing, trilling mess that is hard to describe. All the sounds are there, but it's as if a rapidly stuttering filter of some kind were overlaid? Seems like there must be a simple solution to this -- besides always opening the pulseaudio volume control app?

The output device is listed as imx-hdmi-soc Analog Sterio in the Pulse Audio Volume Control dialog box.

If I go to Xubuntu's Audio Mixer Plugin, the Sound card is listed as the same.

---

### Post by neu5eeCh on 2014-07-04
Okay, I found a similar complaint here:[ HDMI audio works only with pavucontrol]("https://bbs.archlinux.org/viewtopic.php?id=171590")

But the solution still eludes me, even when following the suggested links. Sounds like sampling problem?

---

### Post by neu5eeCh on 2014-07-06
So, I also asked this question in the Multimedia & Video thread, [here]("http://ubuntuforums.org/showthread.php?t=2233098"). I've copy and pasted the answer from there to here and leave it to the mods to decide if these should be merged.

The solution comes from [here]("https://forums.virtualbox.org/viewtopic.php?f=7&t=23982&sid=9e7c182553a4b99535fe943cea20632f&start=30"):

The gist of it is this:

In the /etc/pulse directory are the following files:

 	 		 			 			 				client.conf daemon.conf default.pa system.pa 			 		
 	
 
[B]
Step 1[/B]: sudo nano default.pa

Look for the following lines:

>  	 		 			 			 				Automatically load driver modules depending on the hardware available
Ugly hack for Nexus 10
.ifexists /system/lib/hw/audio.primary.manta.so
load-module module-udev-detect tsched=0
.else
load-module module-udev-detect
.endif 			 		


 	
 
[B]

Step 2[/B]: Hash them all out, and put in the line:

> 
 	 		 			 			 				load-module module-udev-detect tsched=0 			 		
 	
 


So, we're eliminating the if/then statement and invoking the "ugly  hack" that worked for the NEXUS 10, which just happens to work for my  armhf Cubox-i (and might work in other systems).

---

