---
title: "tvtime and sound"
date: 2005-06-11
forum: General Help
---

### Post by Blackie_Chan on 2005-06-11
Sometimes while watching tv using tvtime, the sound will disappear.   It will then appear up to a minute later (other times, every day or so there would be no sound for over 30mins) .  This disappearing sound happens at least once every hour that I use tvtime.

Another thing that happens at times is the sound sounds like the sound you hear when you play a video in slow motion.

So, 99% of the time the sound is good, the other times something happens to the sound.  What can be the reason for this?  How can I fix the problem?

Note: when something happens to the sound in tvtime, I can play music using xmms, and the sound is find.

Thanks in advance.

---

### Post by Blackie_Chan on 2005-07-09
I found a solution to my problem.  I just needed to reload the cx8800 module.  So I ran the following as root ```
modprobe -r cx8800; modprobe cx8800; modprobe -r tuner; modprobe tuner
```

---

