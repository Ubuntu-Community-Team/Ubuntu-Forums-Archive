---
title: "brutal poweroff in linux"
date: 2007-04-12
forum: General Help
---

### Post by brazzmonkey on 2007-04-12
hi there,
i've been a linux user for a couple of years. i'm currently running arch linux on my old desktop computer and kubuntu on my laptop.
one thing i noticed along these past 2 years is that whatever the distribution, whatever the computer, linux poweroff seems "brutal" when compared to windows'.

windows shuts down computers in a gentle, gradual way : HD spin down, fans carry on rotating for one second or two before the computer really shuts down, etc.

in linux, everything shuts down at once (HD, fans, motherboard, etc), in a very harsh noise. this is quite disturbing : on my laptop, windows shuts down silently, linux is very noisy.

my concerns are :
- can it lead to problems regarding hardware lifetime ?
- is there a way to get a smoother shutdown process ?
- anyone noticed similar behaviour ?

thx

---

### Post by Spr0k3t on 2007-04-12
If you watch the process, you will notice everything is being shut down and the drive heads are parking and whatnot.  Once everything signals back to the process the system is ready to shut down, it does so in a single "voice".  On the windows side of things, it just feels like everything is limping along disgruntled about having to go to bed.  Having used computer systems for so many years, I'd rather not have a shut down process, or at least make the process so short that it happens in under a second or two.

On another note, I loved the three second cold boot time with internet connectivity I had at one point... that computer was a beast even for '93.

---

### Post by brazzmonkey on 2007-04-12
so basically i was sort of right, linux shuts down everything at once. i don't have anything against that as long as hardware doesn't suffer.

---

### Post by brazzmonkey on 2007-11-04
i wake this thread up because i noticed shutdown is a lot smoother on gutsy. i suppose this is kernel-related.

---

### Post by bapoumba on 2007-11-04
> **brazzmonkey said:**
> i wake this thread up because i noticed shutdown is a lot smoother on gutsy. i suppose this is kernel-related.
Please check this thread:
[http://ubuntuforums.org/showthread.php?t=508576](http://ubuntuforums.org/showthread.php?t=508576)
I did not follow it up to the end, but there was a kernel bug, yes.

---

### Post by brazzmonkey on 2007-11-04
aw, that's a long thread ! scary also&#8230;

---

