---
title: "No sound in Firefox"
date: 2007-03-25
forum: General Help
---

### Post by fearevilleet on 2007-03-25
HI,

My sound is not working in firefox when I try and see videos from youtube. I dont think it is a flash issue because the video plays fine expect for the sound. I can play sound find in other programs. I did check and make sure the volume in the youtube video is up :}}  Any any have any idea what could cause this issue?

---

### Post by divague on 2007-03-25
Try this

sudo apt-get install alsa-oss

sudo gedit /etc/firefox/firefoxrc

Change:

FIREFOX_DSP=""

To:

FIREFOX_DSP="aoss"

and restar firefox

---

### Post by kiaran on 2007-04-14
> Try this

sudo apt-get install alsa-oss

sudo gedit /etc/firefox/firefoxrc

Change:

FIREFOX_DSP=""

To:

FIREFOX_DSP="aoss"

and restar firefox

I tried this. Still no sound in flash videos (you tube) in firefox. :(

Any other suggestions? (I'm using an Nvidia HDA onboard sound card)

---

### Post by citaworvk on 2007-04-14
I also tried this, and I got this output in terminal:


ALSA lib pcm_direct.c:1477:(_snd_pcm_direct_get_slave_ipc_offset) Invalid value for card


I use USB speakers but sound works fine for avi and mpeg files. No firefox sound, no real player sound.

---

### Post by michaelm66 on 2007-06-17
i thought this might help: i'm using pclos 2007, and i didn't have any sound in firefox while watching you tube videos. i did upgrade the sound system applications because they were marked upgradable in the repository but i didn't touch any configuration files. instead, i installed swfdec-mozilla, swfdec,libswfdec0.3 by synaptic (it says they are flash animation plugins) and firefox is playing both video and the sound.

i find that with media files it is often the problem with plugins, rather than with the system configuration, unless something is really wrongly configured. but if things basically work off the live cd, they should work after installation. it's just the addons and plugins...

---

