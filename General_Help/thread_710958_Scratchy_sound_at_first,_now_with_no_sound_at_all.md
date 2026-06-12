---
title: "Scratchy sound at first, now with no sound at all"
date: 2008-02-29
forum: General Help
---

### Post by napster2500 on 2008-02-29
Hi there! I've really tried all metods here, but i can't make my sound card work in gutsy. At first it was a bit scratchy in the left side, and now, after following this method [here](https://help.ubuntu.com/community/HdaIntelSoundHowto) i am having no sound at all. 
I have a STAC9220/9221 sound card model on my D975XBX Intel Motherboard.
When I type alsamixer in my terminal it says:
> alsamixer: function snd_ctl_open failed for default: No such file or directory


Is there a way to solve this?:)

---

### Post by superprash2003 on 2008-02-29
try this..may work [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by napster2500 on 2008-02-29
tried that.. when i change autodetect, with any other option i get the same error when i test it.

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

Edit: When i try to open the volume control panel i get this error message:

> No volume control GStreamer plugins and/or devices found.

---

