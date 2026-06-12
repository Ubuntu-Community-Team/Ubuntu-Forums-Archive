---
title: "Mplayer Help"
date: 2005-06-15
forum: General Help
---

### Post by parradux on 2005-06-15
I recently installed mplayer, however there is a slight problem. 

I have movies that are backed up in .bin/.cue form. Whenever I try to play them, there is picture however there is no sound. How do I go about fixing this problem? Is it driver related?

I tried playing the movies in Totem, however, they wont even open.

---

### Post by diebels on 2005-06-15
You could use bchunk to convert them to iso images thats a bit easier to work with. Missing sound could be alsa related. Try killing esound or set up mplayer to use esound.

---

### Post by parradux on 2005-06-16
[QUOTE=diebels]You could use bchunk to convert them to iso images thats a bit easier to work with. Missing sound could be alsa related. Try killing esound or set up mplayer to use esound.[/QUOTE]
 How do I do this?

Btw, the error that I get when I try to play any movies on mplayer is this: 

error opening/initializing the selected video_out(-vo) device

---

### Post by parradux on 2005-06-16
bump

---

### Post by diebels on 2005-06-18
To install bchunk, enable universe repository and install with apt-get synaptic or whatever. To use it, run bchunk --help, man bchunk, or something to show you how to use it. To set up gmplayer to use esound, right click it and get into preferences->audio, and select esound driver. Normally xv video driver gives best performance, set it same way you do audio. To kill esound, run gnome-system-monitor, find the esound prosess and kill it.

---

