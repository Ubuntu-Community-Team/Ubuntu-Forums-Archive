---
title: "Skype with headsetd"
date: 2007-12-02
forum: General Help
---

### Post by survient on 2007-12-02
I've been able to get the bluetooth-alsa utilities to work, I can use "headset" or "a2dpd" as their own alsa devices, and record/playback on each. However, for the life of me, I can't seem to get skype to pick up on using "headset" as a device. it either keeps saying:

ALSA lib ../../../src/pcm/pcm.c:2105:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_a2dpd.so

or

ALSA lib ../../../src/pcm/pcm.c:2105:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_sco.so

I checked for these libraries and they are in my alsa-libs folders as valid symbolic links to 
/usr/lib/alsa-lib/libasound_module_pcm_a2dpd.so.0.0.0

The only thing I can figure at this point is that my libraries are 64 bit, and I'm running skype 32 bit, but I'm not sure how to configure things to have the 32 bit bluetooth-alsa libraries installed.

---

### Post by matthewcraig on 2007-12-02
Just going to throw a little whisper in your ear... "Ekiga is part of the Ubuntu operating system by default, works great for Voice over IP, and it runs the open SIP protocol that ties into Google Talk and many other open applications."

---

### Post by survient on 2007-12-02
I'd use a different program for VOIP going from a computer to another one, but I'm getting set up to have the full skype package to replace my existing cell phone service. Besides, skype runs fine by itself, I'd just like to get it running with my bluetooth headset. I'm just not sure what the issue is. I don't believe it's a 32-64 bit incompatibility issue, because skype runs fine with 64 bit versions of alsa and related libraries.

---

### Post by matthewcraig on 2007-12-02
Have you talked with the Skype support?  They are the only ones who have access to that closed-source code.

---

### Post by survient on 2007-12-02
It's not a direct skype issue, it's an issue with the bluetooth-alsa libraries, I'm not sure how or where to put the 32 bit libraries, or if I even need them.

---

### Post by tpol on 2008-02-01
Were you able to figure this out, Survient?  I'm having precisely the same issue.  Thanks.

---

### Post by survient on 2008-02-01
Not yet, skype is closed source, and it looks like it only will allow you to select alsa devices it recognizes, the headsetd not being one of them.

---

