---
title: "totem wmv problem"
date: 2005-04-24
forum: General Help
---

### Post by nigel on 2005-04-24
Ok I'm not 100% sure this is the correct forum but here goes


to start with
I installed the following during my first day of ubuntu tinkering
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install w32codecs
sudo apt-get install xine-ui

after this I couldn't play wmv at all and avi's just gave sound,
So, I uninstalled totem-gstreamer and then installed totem-xine, 
then
AVI's worked fine and wmvs had no sound 
So after searching the forum I changed a setting in *xine/catalog.cache* from *"decoder_priority=1" to "decoder_priority=7"*  this made sound work in some .WMVs but in others all I got was the picture with no sound, all work under windows Media player( in windows obviously), but I can't seem to work out what the problem is here

any help would be greatly appreciated

---

### Post by Burgundavia on 2005-04-24
There are some known bugs with wmv and sound. This may also effect other apps that use w32codecs.

Corey

---

### Post by microo on 2005-04-30
Hi Nigel,

I'm really new to Linux ...can you tell me what you have done to change the setting in /xine/catalog.cache ..to change the priority of the decoder.


I hope you will this !!


Thanks

---

