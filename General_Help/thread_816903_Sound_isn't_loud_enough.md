---
title: "Sound isn't loud enough"
date: 2008-06-03
forum: General Help
---

### Post by Colro on 2008-06-03
I've tried turning up every single control for ALSA, OSS, and PulseAudio and my sound still isn't as loud as I can get it on other distros and windows. It's not at a point where I can't hear it, but it's annoying when I try to watch movies from a more distant part of the room. I've tried switching to ALSA/OSS/PulseAudio instead of AutoDetect as well with no real results -- OSS was a little louder, but still not what I'm trying to achieve. Is there some kind of volume safety lock that I'm missing here? I'm currently testing it with headphones -- does that make a difference at all? Any help would be appreciated :)

Here's what lshw gives me for my audio device:


```
id:	
multimedia
description: 	Audio device
product: 	MCP55 High Definition Audio
vendor: 	nVidia Corporation
physical id: 	
6.1
bus info: 	
pci@0000:00:06.1
version: 	a2
width: 	32 bits
clock: 	66MHz
capabilities: 	pm msi ht bus_master cap_list
configuration:	
driver	=	HDA Intel
latency	=	0
maxlatency	=	5
mingnt	=	2
module	=	snd_hda_intel
```

---

### Post by Colro on 2008-06-03
bump

---

### Post by Colro on 2008-06-04
bump

---

### Post by Colro on 2008-06-08
bump

---

### Post by Colro on 2008-06-08
bump

---

### Post by Colro on 2008-06-09
bump

---

### Post by Colro on 2008-06-09
bump!

---

### Post by Avenger1432 on 2008-06-09
Sry it is taking long for someone to respond to you,  wish i could help but i know nothing lol...  

gets frusturating, after a couple hours your thread get pushed to the 2nd or 3rd page where noone would look.

---

### Post by Yellow Pasque on 2008-06-09
Make sure your alsa-base file is configured correctly: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

---

### Post by Unix_Slayer on 2008-06-09
Open your mixer, and make sure the slides are up to max on the master channel. Could be just one slide doing it. Are all the sounds low, including Ubuntu sounds? You might have to change the master to another channel.

---

### Post by nazcatati on 2009-01-25
I don't know if you already found the solution but I came across a solution that worked for me on google and thought I should post in case someone else has the same problem.

Solution:

1. Right-click Applications, choose Edit Menu. 
2. Select Sound & Video.
3. Put a check mark in Volume Control. 
4. Click Apply or Close. 

Then just go to Applications > Sound & Video > Volume Control

After that.. I raised all the bars and that basically fix it.

---

