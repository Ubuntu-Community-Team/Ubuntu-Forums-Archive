---
title: "Wmv"
date: 2007-04-05
forum: General Help
---

### Post by GuitarRocker2562 on 2007-04-05
How do I get totem to play wmv videos, it will play the audio, but no video.
Also, in mplayer, if I view a video in fullscreen the video stays at it's original resolution, it won't stretch, any fixes?

---

### Post by Shmifty on 2007-04-05
w32codecs?

---

### Post by tbroderick on 2007-04-05
With mplayer, you might have to change your video ouput to xv or something else like gl or gl2.
```
mplayer -vo xv file.avi
```

Hit 'f' for fullscreen. You can also change the settings using the GUI.

---

### Post by GuitarRocker2562 on 2007-04-05
thanks, xv works fine!

how do I install the w32 codecs?

remember I run feisty

---

### Post by tbroderick on 2007-04-05
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Maestro23 on 2007-04-05
> **GuitarRocker2562 said:**
> thanks, xv works fine!

how do I install the w32 codecs?

remember I run feisty

Synaptic(GUI): Search w32codecs.  Mark for install.

Command line:

> sudo aptitude install w32codecs


---

### Post by GuitarRocker2562 on 2007-04-05
I extracted the win32 codecs to /usr/lib/win32/ the video plays fine in mplayer, but in totem I just get a black screen with audio. Help?

---

### Post by tbroderick on 2007-04-05
totem uses gstreamer plugins not w32codecs. Not all wmv wil play in totem. Mplayer of Xine is best for wmv.

---

