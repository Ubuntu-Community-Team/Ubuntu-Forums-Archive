---
title: "There Must Be SOMETHING That'll Play Live BBC Streams"
date: 2007-01-11
forum: General Help
---

### Post by Mark76 on 2007-01-11
Other than Realplayer. 

For God's sake ](*,)

---

### Post by Mark76 on 2007-01-11
Never mind.  I finally worked out how to open the Windows Media file in Kaffeine :redface:

---

### Post by Bloch on 2007-02-16
How do you get RealPlayer to play them? I can't get anything to play them.
I have RealPlayer 10.0.8.805 installed with Automatix. It plays sound with no image. Same on the RTE site

[http://www.rte.ie/](http://www.rte.ie/)

It's driving me nuts because over the past year streaming media works, then it doesn't, then it does again when I fiddle something . . .

The RealPlayer plugin is ther (with the logo) and there is sound but no video - what has changed since the last time it worked?

Can someone check either of these sites and see if they work?

---

### Post by Red Knuckles on 2007-02-18
I got video and sound from [http://www.rte.ie/](http://www.rte.ie/) and [http://www.bbc.com](http://www.bbc.com) now. The mplayer plugin is playing video with sound. For the radio pages I uninstalled RealPlayer and installed gxine, gxine-plugin, kaffeine-plugin. For these 2 websites gxine works for me. For [http://www.npr.org](http://www.npr.org) kaffeine works.
:lolflag: :guitar:

---

### Post by Red Knuckles on 2007-02-18
I've just figured out how to get sound from RealPlayer in Firefox and Swiftfox:

sudo aptitude install alsa-oss
sudo kwrite /usr/lib/realplay-10.0.8/realplay

edit this line [It's line 73]

$REALPLAYBIN "$@"

to read:

aoss $REALPLAYBIN "$@"

reboot and you should have sound in RealPlayer on the mentioned web sites.
:lolflag: :guitar:

---

### Post by TimL on 2007-03-18
> **Red Knuckles said:**
> I've just figured out how to get sound from RealPlayer in Firefox and Swiftfox:

sudo aptitude install alsa-oss
sudo kwrite /usr/lib/realplay-10.0.8/realplay

edit this line [It's line 73]

$REALPLAYBIN "$@"

to read:

aoss $REALPLAYBIN "$@"

reboot and you should have sound in RealPlayer on the mentioned web sites.
:lolflag: :guitar:

Thanks Red Knuckles, this worked perfectly for me (no need for a reboot though, just restart RealPlayer).

---

### Post by Red Knuckles on 2007-03-19
> **TimL said:**
> Thanks Red Knuckles, this worked perfectly for me (no need for a reboot though, just restart RealPlayer).

Always glad to help.

---

