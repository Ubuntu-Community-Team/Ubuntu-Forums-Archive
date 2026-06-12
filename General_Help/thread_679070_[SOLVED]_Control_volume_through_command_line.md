---
title: "[SOLVED] Control volume through command line"
date: 2008-01-26
forum: General Help
---

### Post by eapache on 2008-01-26
I have a keyboard with volume controls, and I'm using fluxbox keys.

I know how to use amixer to set my sound device to a fixed volume, but I want to know if it is possible to set it to a relative volume instead.

I imagine it would be possible to write a bash script that gets the current volume from amixer, and uses that to set an absolute volume which is relative to my current volume, but that is beyond my scripting abilities.

---

### Post by Whiffle on 2008-01-26
on mine....

aumix -v -2  

takes the volume down 2%.  aumix is in apt, although I dunno if they've gotten around to fixing that package yet.

---

### Post by eapache on 2008-01-26
It doesn't seem to work. Whenever I run it, it just prints

aumix: SOUND_MIXER_READ_DEVMASK

and exits without actually changing anything.

---

### Post by Whiffle on 2008-01-26
Yep, that package is still broken.  Go ubuntu :rolleyes:

Apparently if you recompile it from source, it works.  

I think the way to do that is
apt-get source -b aumix

and if it doesn't install it after its built it, then
dpkg -i aumix....deb

---

### Post by eapache on 2008-01-26
I found the launchpad report, where someone has uploaded a repackaged version that works. It's exactly what I was looking for. Thank you!

---

### Post by sisco311 on 2008-01-26
> **eapache said:**
> I have a keyboard with volume controls, and I'm using fluxbox keys.

I know how to use amixer to set my sound device to a fixed volume, but I want to know if it is possible to set it to a relative volume instead.

I imagine it would be possible to write a bash script that gets the current volume from amixer, and uses that to set an absolute volume which is relative to my current volume, but that is beyond my scripting abilities.

read the man page:
```
man amixer
```>  When plus(+) or minus(-) letter is
              appended after volume value, the volume is incremented or decre&#8208;
              mented from the current value, respectively.```
amixer -c 0 set PCM 3%+
amixer -c 0 set PCM 3%-
```

---

### Post by cknight on 2008-01-26
Part of my fluxbox keys tutorial covers this exact scenario...

[http://ubuntuforums.org/showthread.php?t=617812]("http://ubuntuforums.org/showthread.php?t=617812")

Good luck!

---

### Post by humble_coffee on 2008-06-09
yeah amixer is the way to go out of these. It was simple for me to hook it up to my remote with lirc. I'm curious though, shouldn't there be a way to run whatever commands are run when you press whatever hotkeys you've associated with the volume controls via gnome? That way you'd get the funky looking visual display of the state of your volume on the screen. It's certainly desirable when you're adjusting the volume from across the room.

---

