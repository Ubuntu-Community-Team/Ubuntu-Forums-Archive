---
title: "PulseAudio choppy after swap used - can I 'lock' it into RAM?"
date: 2013-05-15
forum: General Help
---

### Post by NTL2009 on 2013-05-15
Xubuntu 12.04 (though I don't think this is specific to xfce) - recently I added the equalizer (qpaeq) and it seems that the audio gets a little choppy (seems like all sources, youtube, movieplayer, etc) after I have loaded a bunch of tabs/windows and have used some swap space (my laptop is maxed at 3GB RAM). Even after I clear out some memory, the choppiness continues. I've found that killing pulseaudio and letting it restart clears it up, until I use up RAM and go to swap again.

I'm wondering if it would help if I could 'lock' PulseAudio into RAM? I'm assuming it, or some component is getting moved to swap, and slowing things down? Is there a way to do this (not the over-all 'swapiness' command, but specific to PulseAudio and it's components)?

Or is there another solution?

-NTL2009

---

### Post by CatKiller on 2013-05-15
There are memory-management and priority options in PulseAudio's config files. Not at my computer, so I can't tell you exactly what they are, but the man pages will help.

---

### Post by NTL2009 on 2013-05-15
Thanks. I'm not too good finding my way around config files, but I see a " lock-memory = yes/no " as an option in the man page, and RECOLL (yeah RECOLL!!!!) found that in  /etc/pulse/daemon.conf and default was 'no'. I edited that to 'yes', will re-boot and test it out and report back. I'm assuming daemon.conf is the right file for an app that loads at start-up.

OK, rebooted, loaded up memory until it has loaded up on swap and running like a slug on every new window and so far so good! Will probably need a few days to fully verify this, it was fairly subtle, but not so subtle that I could ignore it.

Is there any way to tell which processes are pushed out to swap (or whatever the correct term is)?

-NTL2009

---

### Post by CatKiller on 2013-05-16
Glad to hear it's working for you.

> **NTL2009 said:**
> 
Is there any way to tell which processes are pushed out to swap (or whatever the correct term is)?

If there is I don't know it, I'm afraid.

---

