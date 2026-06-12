---
title: "dosemu-freedos crashes"
date: 2006-07-21
forum: General Help
---

### Post by stimpsonjcat on 2006-07-21
Hi

I need some help with dosemu-freedos. It won't start. I get this error:

```
ERROR: coopthreads: lowmem heap + stack are too big
leavedos(99|0x63) called - shutting down

```

I also had the problem described in [this breezy thread]("http://www.ubuntuforums.org/showthread.php?t=112952") before. It's a pity that wasn't fixed for dapper. ](*,) 

I need freedos because I want to print some stuff from an old DOS program to a parallel printer and AFAIK dosbox won't let me do that.

Thanks :) 
stimpy

There is a bug report on launchpad [here]("https://launchpad.net/distros/ubuntu/+source/dosemu/+bug/53384").

---

### Post by stimpsonjcat on 2006-07-21
OK, I got it to work finally. For future reference: There is a debian bug report about this [here]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=327153").
Replacing the comcom.com :rolleyes: file as described fixed the issue for me.

---

