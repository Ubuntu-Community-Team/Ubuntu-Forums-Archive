---
title: "Sound very quiet on Edgy RC"
date: 2006-10-20
forum: General Help
---

### Post by unlokia on 2006-10-20
Hi!

I have just installed Edgy Eft RC i386 - the livecd sound levels are fine, but my INSTALLED sound system is SO SO quiet...

what have I done wrong?:???: 

If anyone can tell me how I reset the sound system...

:D Hey thanks!

<<<< EDIT!! >>>>

Duuuh Im so stupid - I fixed it - had volume control set to ALSA and not OSS duuuuh :rolleyes:

---

### Post by soop on 2006-10-20
dbl click your volume icon and make sure your pcm volume level is higher up ...


aside from that .... not sure but I noticed low volume and then realized my pcm volume was low

---

### Post by russianbandit on 2006-10-20
Same thing here (Kubuntu RC) and my PCM looks good (at about 85% of the slider).

---

### Post by raqball on 2006-10-20
Also....

In terminal type:

alsamixer

Make sure your volumes are cranked. Move left to right with arrow keys. Also if it displays 'mm' it's muted. hit m to unmute that option

Up and down arrow keys to raise or lower the volume.

When done hit Esc....

Volume is now louder :)

---

