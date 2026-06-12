---
title: "OVH dedi server 32bit or 64bit - which should i use?"
date: 2008-07-04
forum: General Help
---

### Post by garethsimpsonuk on 2008-07-04
Hi, 

I'm just in the process reinstalling my OVH dedi server with Hardy server. I've done it a couple of times and I've always picked 32 bit. I've never used 64 bit and as I'm still a learner I didn't want to complicate thing more.

Now I'm wondering whether I should go with 64 bit but what's the main differences?

Will 64 give me a big performance boost?

Will all my software still be compatible? - Do I have to find 64 bit versions of programs I use? Or will 32 bit software work on it?

Is everything still the same in the OS? Commands / Layout the same?

So basically, is it worth making the change? My server is only 1GHZ + 1GB ram and it has buckled when I've pushed it too far? ( it's for personal use only - seedbox / web dev etc.

Any opinions / advice are appreciated,
Thanks

-- edit--

I took the plunge and chose 64. Since then I have read things like this - 

64 is only a big advantage with virtualization and big RAM systems.

Compiling / making from source has it's problems if software is designed for 32 bit.

Should I reinstall 32? This is what I run on the server- LAMP, Torrentflux-b4rt, Jinzoora, A few other html / php apps, webmin, and a few more amazing apps I've yet to discover.

I don't recall any of this software having a specific 64 port. Are the repos the same as 32? I install flux, webmin and jinzoora manually.

Thanks

---

### Post by garethsimpsonuk on 2008-07-04
well after the updates the first thing i tried to install was webmin. I recieved dependency issues. 32 bit it is then

edit: it turns out it was my fault after all lol. Installed dependencies and it's fine. i'll give the 64 bit a trial run

---

### Post by garethsimpsonuk on 2008-07-04
> 
Package python-psyco is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python-psyco has no installation candidate
root@ks361702:~#


I recieved this while installing flux-b4rt. I think it's best to just go back to 32bit rather than get far down the line and something doesn't work. I haven't got the patience or the time at the moment and it's only a seedbox. I think I'll switch to 64 when it's caught on a bit more.
So there's my short live experience for you guys lol

---

