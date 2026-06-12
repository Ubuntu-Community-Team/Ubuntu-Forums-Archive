---
title: "Left Speaker Issues"
date: 2007-02-10
forum: General Help
---

### Post by Rab22 on 2007-02-10
Okay, I don't exactly know how this happened, but...it's really confusing.

While in XFCE I loaded up the sound mixer to change the volume and I lost my left speaker. My right speaker is working just fine, but the left one went out. 

I have two sound cards, an onboard and a PCI. The onboard works fine -- both speakers that is. However, on the PCI one, this is not the case. I know the card has no trouble since I can boot into another install and it works just fine.

So I loaded up alsamixer thinking that one channel was muted -- nope. I verified this in GNOME's Alsa Mixer as well. I've unlinked them and moved them around and nothing. 

I'm really confused; how could this have just 'happened'. Does anyone know of any bugs within XFCE's mixer that mutes a channel? And if so, does anyone know how to fix it?

Whenever I resolve the issue, I'll post the solution.

Thanks...

---

### Post by Rab22 on 2007-02-10
Figured it out.


It appears that the mixer changed the "H/W" from 'PCM Out' to something else. It, however, did not change the "H/W 1" so the right channel was fine. 

If anyone else has any issues with this, you can find it by scrolling all the way to the right in alsamixer.

---

### Post by maldek on 2007-05-19
The same thing just happened to me but I don't see what you're talking about in alsamixer.  Can someone explain it a little differently?

---

### Post by maldek on 2007-05-19
Bump. Sorry, but I really can't figure out how to get my sound back in the left speaker.

---

### Post by Rab22 on 2007-05-19
> **maldek said:**
> Bump. Sorry, but I really can't figure out how to get my sound back in the left speaker.

```
sudo alsamixer
```

Once in alsamixer (if you have multiple sound cards, you'll need to give it an interface), keep scrolling to the right until you see "H/W" and "H/W 1".  Just above that you'll see text.  For mine to work properly, that text has to be on "PCM Out".  You can scroll through the text by using the up/down arrows.

I hope this helps -- best of luck!

---

### Post by maldek on 2007-05-19
That's the problem, scrolling all the way to the right I don't see any H/W anywhere.

---

