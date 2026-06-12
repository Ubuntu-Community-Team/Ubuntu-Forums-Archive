---
title: "Mplayer: picture lagging behind sound"
date: 2004-11-05
forum: General Help
---

### Post by ming0 on 2004-11-05
I've got about a 1/4 second lag in video behind sound--this is only in Mplayer... Wxvlc doesn't have this problem, but the zoom feature in wxvlc is really pixelated. How do I get Mplayer to sync up correctly?

I've tried messing w/ some of the autosync settings, but nothing seems to help!


PS this is w/ all types of video files, and I have a dual proccessor Athlon 1.2 setup, so it's not for lack of proccessing power or corrupted media.

Thanks :)

---

### Post by im_ka on 2004-11-06
do you have mplayer for c. marillat's repo?
have you tried playing around with the video settings and codecs?

---

### Post by cseg on 2004-11-06
mplayer -framedrop

---

### Post by wallijonn on 2004-11-06
It could be as simple as IRQ sharing under MSWindows. I used to have to move the sound card from the nic IRQ to do away with stuttering. 

Try your soundcard in another slot, if possible. If you are using built in sound, you may be fluxed.

---

### Post by ming0 on 2004-11-11
Thanks for the tips--I added the following in my ~/.mplayer/config file:
```

# Write your default config options here!
framedrop=yes
cache=8192
zoom=yes

```
seems to have done the job.

---

