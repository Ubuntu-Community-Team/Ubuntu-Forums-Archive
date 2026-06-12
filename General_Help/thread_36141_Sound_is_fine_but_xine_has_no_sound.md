---
title: "Sound is fine but xine has no sound"
date: 2005-05-22
forum: General Help
---

### Post by mira-ceti on 2005-05-22
I am using Hoary 5.04

I have sound working in Totem when I  play an avi.  

When I try watch the same avi in xine I get the message. 

"Unsuupported Codec  Audio codec  MPEG Layer 2/3 (0x55)". 

I want to use xine, as Totem has a sound sync problem and it makes viewing avis less than plesant.

Clearly Totem has access to the codec but I cannot locate it in the Totem preferences or configuration file.

So.

 I have installed every mpeg and win32 codec I can find in the /usr/lib/win32 folder and xine is configured to search there for codecs.  Does anyone know where I can get this illusive codec, or is it possible that xine is lying to me and there is some other problem.

Thanks  Bevan

---

### Post by bored2k on 2005-05-22
[QUOTE=mira-ceti]I am using Hoary 5.04

I have sound working in Totem when I  play an avi.  

When I try watch the same avi in xine I get the message. 

"Unsuupported Codec  Audio codec  MPEG Layer 2/3 (0x55)". 

I want to use xine, as Totem has a sound sync problem and it makes viewing avis less than plesant.

Clearly Totem has access to the codec but I cannot locate it in the Totem preferences or configuration file.

So.

 I have installed every mpeg and win32 codec I can find in the /usr/lib/win32 folder and xine is configured to search there for codecs.  Does anyone know where I can get this illusive codec, or is it possible that xine is lying to me and there is some other problem.

Thanks  Bevan[/QUOTE]
 Did you make sure xine is using esd sound client ? in its settings, make urself master of the known universe > audio > esd.

Also, might want to try install gxine and vlc vlc-esd /

---

### Post by mira-ceti on 2005-05-22
Firstly, thanks for your help I appreciate your efforts.

I have tried setting xine to use esd audio and also installed gxine but still no sound.  I cannot install vlc it returns dependancy problems :(

---

### Post by mira-ceti on 2005-05-22
Just some more info, this is a copy from gxine "xine engine log output"

xine: found demuxer plugin: Elementary MPEG stream demux plugin
xine: found input plugin  : file input plugin
audio_decoder: no plugin available to handle 'MPEG layer 2/3'
xine: found demuxer plugin: AVI/RIFF demux plugin
xine: found input plugin  : file input plugin
xine: found demuxer plugin: Elementary MPEG stream demux plugin
xine: found input plugin  : file input plugin

---

### Post by abovett on 2005-06-11
[QUOTE=mira-ceti]
audio_decoder: no plugin available to handle 'MPEG layer 2/3'[/QUOTE]
Hi

I'm getting this too on a couple of recent Ubuntu installs. However, all my older installs (3 or 4) play MPEGs fine with Xine.

Can't see any obvious difference in the packages installed - searched for "xine" and "mpeg" in synaptec and checked that the installed packages were the same, and w32codecs is installed on all of them.

Did an strace on a good and bad system too, but to be honest I'm not very familiar with using it and there's so much there that I can't figure out what's going on.

Anyone got any ideas? I'm selling one of the PCs to a friend and I'd really like to let her have it with Ubuntu on it but if I can't get good multimedia playback I'll have to consider another distro - I really want to crack this but I can't keep her waiting forever!

Regards

Andy B

---

### Post by abovett on 2005-06-12
I believe I've found the elusive package that provides the decoder Xine needs for  'MPEG layer 2/3' (why do there have to be so many MPEG decoder packages?!). It's called **libmad0**. The reason it took so long to find is that there are many packages with "mpeg" in the name, but this isn't one of them (however, at least one of them does depend on this one).

Hope that helps anyone else with the same problem.

Andy B

---

### Post by salladen on 2005-08-31
Yes! thank u very much. That was the missing package.    \\:D/

---

### Post by terrapin28 on 2005-10-06
Thank you,
I searched for almost two days trying to fix this problem. Funny, I did all the same stuff you did but could not locate the proper library package.
I know that ubuntu's philosophy is all about open source and free software. Mp3 playback is such a core of todays multimedia. Maybe an easier route should be made for Ubuntu's multimedia experience.

---

