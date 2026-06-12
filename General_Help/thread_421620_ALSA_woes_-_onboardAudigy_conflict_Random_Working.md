---
title: "ALSA woes - onboard/Audigy conflict Random Working"
date: 2007-04-24
forum: General Help
---

### Post by hayzeus on 2007-04-24
I've  read many threads on this subject but have never seen any conclusive answers, so I apologize if I am abusing the forums.

The main problem is that Sound on my computer works only sometimes. After a kernel update it will work for that session but after a reboot will be gone.

I thought I had it working yesterday (I unmuted everything put volumes up to full) but I booted today and sound once again was gone.

Now when I go into ALSA mixer the onboard is the mixer that shows up (when yesterday it was the Audigy)

I'm really at the end of my tether. I just want sound to work.

---

### Post by nintendophile on 2007-04-24
I've had a similar problem, the work around I found;

```
tgrime@heisenberg:~$ asoundconf list
Names of available sound cards:
I82801DBICH4
Audio
tgrime@heisenberg:~$ sudo asoundconf set-default-card Audio
```

Obviously replace Audio with the name your card, i.e. the non onboard sound card

When I do this alsamixer shows my usb sound card, everything works as it should.
I imagine it's possible to write a script to do this automatically with hotplug, but I've yet to figure this out

---

