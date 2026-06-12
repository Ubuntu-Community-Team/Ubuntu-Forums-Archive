---
title: "I have sound ...but NOT all sound app's working"
date: 2005-04-13
forum: General Help
---

### Post by iminj on 2005-04-13
Pentium II 266MHz - 192Mb RAM
nvidia - RIVA 128
Sound Blaster 16
Ubuntu "Hoary" 

I added "snd-sbawe" to etc/modules and I have sound. I have 2 mixers
(0) CTL1745 (OSS Mixer)
(1) SoundBlaster16 (Alsa Mixer)

Here's a rundown of what works, and what doesn't:

System Sounds are **OK**
Audio CD's are **OK** with CD Player
DVD sound and video is **OK** with Totem Movie Player
Streaming Audio is the problem. With Streamtuner .. here's what happens:


When configured for xmms - **NO SOUND ** .... and xmms freezes
When copnfigured for beep media player - **NO SOUND**
Configured for musicplayer is **OK** - i get sound

I'd prefer to use beep or xmms. Anyone able to help me troubleshoot this?


-iminj

---

### Post by Astrophobos on 2005-04-13
[QUOTE=iminj]Pentium II 266MHz - 192Mb RAM
nvidia - RIVA 128
Sound Blaster 16
Ubuntu "Hoary" 

I added "snd-sbawe" to etc/modules and I have sound. I have 2 mixers
(0) CTL1745 (OSS Mixer)
(1) SoundBlaster16 (Alsa Mixer)

Here's a rundown of what works, and what doesn't:

System Sounds are **OK**
Audio CD's are **OK** with CD Player
DVD sound and video is **OK** with Totem Movie Player
Streaming Audio is the problem. With Streamtuner .. here's what happens:


When configured for xmms - **NO SOUND ** .... and xmms freezes
When copnfigured for beep media player - **NO SOUND**
Configured for musicplayer is **OK** - i get sound

I'd prefer to use beep or xmms. Anyone able to help me troubleshoot this?


-iminj[/QUOTE]
For xmms, try to set the audio output plugin to esound in preferences

---

### Post by iminj on 2005-04-13
[QUOTE=Astrophobos]For xmms, try to set the audio output plugin to esound in preferences[/QUOTE]

**Thanks** Astrophobos !! 

esound output plugin was the answer. Streaming sound now works in xmms AND configuring the esound plugin setting also works for beep-media-player too. 
The ubuntu community is terrific. 

-iminj

---

### Post by graigsmith on 2005-04-13
i was having similar problems with my usb soundblaster.  so i swapped it out with a sound blaster live, and everything works great now.  the soundblaster live has a hardware mixer. and my usb soundcard doesn't

---

### Post by usererror on 2005-04-15
[QUOTE=graigsmith]i was having similar problems with my usb soundblaster.  so i swapped it out with a sound blaster live, and everything works great now.  the soundblaster live has a hardware mixer. and my usb soundcard doesn't[/QUOTE]

I have a similar problem but i cannot get DVD Audio to work in totem or regular xine.  any ideas?  when I play a dvd movie in xine, it writes the audio to a .wav file in my home directory.  :roll:

---

### Post by doc_holiday on 2005-04-16
Thanks!!

---

