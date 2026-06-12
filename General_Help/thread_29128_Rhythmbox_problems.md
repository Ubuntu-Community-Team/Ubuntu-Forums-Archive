---
title: "Rhythmbox problems"
date: 2005-04-23
forum: General Help
---

### Post by GrayFox^ on 2005-04-23
I just installed Ubuntu Hoary a few days ago and just decided to try to use the included music player (Rhythmbox). The problem is that I imported some songs (which worked a charm) but whenever I try to play the songs I get 2 error windows.

1. Could not pause playback.
2. Could not open resource for writing.

Please help me out.  ](*,)

---

### Post by doclivingston on 2005-04-23
If you're trying to play MP3s you'll need to see [https://www.ubuntulinux.org/wiki/RestrictedFormats](https://www.ubuntulinux.org/wiki/RestrictedFormats) to find out how to install support for them.

---

### Post by fordfan753 on 2005-04-23
You'll need libmad and the -dev file for it to play mp3s with Rhythmbox, these should be easy to find in synaptic or apt-get install

---

### Post by GrayFox^ on 2005-04-30
thanks for the help but i have another question. How do I change the default player of mp3s? Whenever i open one, totem movie player runs it when i want rhythmbox to play it, thanks

---

### Post by Professor X on 2005-04-30
Right click on an mp3 and select properties.  Then click the select the open with tab and select rhythmbox.

---

### Post by groovywombat on 2005-09-06
I have the same problem except everything was working fine (until my eternal fw hdd stopped auto mounting)  I've tried reinstalling rhythmbox and all the gstreamer plugins, but it still refuses to play any files, even ogg files.  any ideas?
thanks

---

### Post by psychicdragon on 2005-09-07
Rhythmbox gives the same error if esd is dead.```
killall esd
esd &
```That should solve your problem.

---

