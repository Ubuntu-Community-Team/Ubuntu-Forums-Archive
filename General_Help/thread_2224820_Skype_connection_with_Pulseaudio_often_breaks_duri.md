---
title: "Skype connection with Pulseaudio often breaks during suspend-resume"
date: 2014-05-18
forum: General Help
---

### Post by halfbeing on 2014-05-18
Very often I find that Skype no longer produces any in-call sounds (it still produces those sounds that are treated as system alerts). If I try to ring another user a window pops up for that call, but the call does not reach the other party and there is no ringing sound. I also miss calls, so it seems like it doesn't ring on incoming calls. Although it is hard to monitor for this behaviour systematically, I am pretty sure that it occurs after suspending and waking the computer. It does not occur every time I suspend the machine, but as far as I can tell, it occurs more often than not.

I use XFCE and so I don't use the Skype wrapper for Unity. I always launch Skype from a copy of the launcher installed with the package, i.e. with the command "env PULSE_LATENCY_MSEC=60 skype %U".

Is my guess that the problem is to do with suspending and resuming right? Is there anything I can do about it to make sure that I don't have to stop and restart Skype after most suspends in order to remain contactable?

---

