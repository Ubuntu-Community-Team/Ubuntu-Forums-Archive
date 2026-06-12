---
title: "Alsa Problems"
date: 2008-05-07
forum: General Help
---

### Post by Statix0 on 2008-05-07
I'm setting up my .asoundrc to work with a wined Ventrilo, and I'm having some problems.

What I'm trying to do is combine both my main sound card (hw:0,0) and my usb microphone (hw:1,0).

Here is my current asoundrc which I stole from [this](http://alsa.opensrc.org/index.php/Asym) page and minimally edited to use hw:1,0 instead of hw:0,0 for dsnoop. I don't know much about asoundrc editing, but this seems like a good start since it's sorttta working.

```
   #asym fun start here. we define one pcm device called "dmixed"
   pcm.dmixed {
       ipc_key 1025
       type dmix
       slave.pcm "hw:0,0"
   }
   
   #one called "dsnooped" for capturing 
   pcm.dsnooped {
       ipc_key 1027
       type dsnoop
       slave.pcm "hw:1,0"
   }
   
   #and this is the real magic
   pcm.asymed {
       type asym
       playback.pcm "dmixed"
       capture.pcm "dsnooped"
   }
   
   #a quick plug plugin for above device to do the converting magic
   pcm.pasymed {
       type plug
       slave.pcm "asymed"
   }
   
   #a ctl device to keep xmms happy
   ctl.pasymed {
       type hw
       card 0
   }
   
   #for aoss:
   pcm.dsp0 {
       type plug
       slave.pcm "asymed"
   }
   
   ctl.mixer0 {
       type hw
       card 0
   }
```
Through audacity only using dsp0 works (alsa-oss) (and of course direct hw1,0 recording works) and with ventrilo only using oss for sound works. Of course this is unacceptable because I need dmix. :)

If it helps, my microphone only records directly in audacity when it is set to mono (1 channel). That... might be the problem? In any case I don't know how to resolve it.

---

