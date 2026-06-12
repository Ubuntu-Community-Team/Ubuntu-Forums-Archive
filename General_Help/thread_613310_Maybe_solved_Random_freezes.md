---
title: "Maybe solved? Random freezes"
date: 2007-11-14
forum: General Help
---

### Post by jfernyhough on 2007-11-14
Following the final release of Gutsy I've had random freezes - background tasks would be running (music playing, sshd running) but the screen would freeze (maybe with mouse control, maybe not, no keyboard control). First I thought it was the Nvidia driver (so moved from the repo to Envy), then I thought it was Firefox (so tried Gran Paradiso, Bon Echo, repo Firefox), then I thought it was Pulseaudio, then I thought it was Pidgin.

Following a hint in another of the many 'Random freeze' threads - and I'm sorry I can't remember which so I can credit this - I installed the 386 kernel instead of the generic ($ aptitude install linux-386).

And touch wood, this seems to have solved the random freezes. I've done everything I normally would. No freezes, no black screen flashes (it even seems as if FF is more responsive when scrolling).

Needs some more testing to check this, but it may be the kernel that is the root of the many problems people are having.

--edit
Found the post - credit to r0bb3d here: [http://www.ubuntuforums.org/showthread.php?p=3755968#post3755968](http://www.ubuntuforums.org/showthread.php?p=3755968#post3755968)

---

### Post by chiselwright on 2007-11-30
You're definitely onto something here.

I've been using the -generic kernels (to make the most of my dual-core CPU).

I've been able to run the "nv" driver without any random freezes at all ... I just lose the ability to suspend/resume successfully.

I've been able to run the "nvidia" driver (with and without compiz) most of the time ... as long as I don't open firefox. As soon as I open firefox, I get anywhere from 0 to 5 minutes before the machine freezes.
(A shame really, because most of the work on my laptop is a webapp I'm working on.)

A couple of days ago I switched to the -386 kernel, nvidia driver and compiz goodness. I haven't had a single random freeze. I put it through its paces, opening up firefox, whirling the desktop cube around a bit ... then back to the normal development I've been doing.

Not a single lock-up.

The downside is I don't benefit from the dual-core goodness any more.
The upside is that I get to use my machine for more that 2 minutes without it locking up.

Thank you so much for finding the referenced post and sharing it here - this issue has been driving me insane!

---

