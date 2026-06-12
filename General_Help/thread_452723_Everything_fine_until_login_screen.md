---
title: "Everything fine until login screen"
date: 2007-05-23
forum: General Help
---

### Post by Timtro on 2007-05-23
Hi All,

I recently had a bit of a hardware issue. I think something was lose, but now its fine, or so I thought. My sound card wasn't working. I just decided to move it a couple of slots down. I powered down the computer, and for some reason ubuntu would 'unload' at the splash, but then hung and did nothing. I powered off manually.

I moved the card, restarted and now I can't get the log in prompt. Black screen instead. Signal is getting to monitor (not sleeping), but its blank.  Everything is fine before this. I can ssh in, and sudo shutdown -P now, and the splash comes up again, shows ubuntu unload and then powers off.

Any ideas?

Could it be a hardware issue with my vid card? I think it's what has been acting up.

Cheers,


Tim.

P.S.

top shows Xorg using 100% (99.9%) of CPU.

Update:

sudo dpkg-reconfigure xserver-xorg  ... same problem.

I'm using fglrx drivers, if that helps anyone.

---

### Post by vtel57 on 2007-05-23
Edit your xorg.conf to run with vesa drivers temporarily and see if you can get X to behave that way.

---

