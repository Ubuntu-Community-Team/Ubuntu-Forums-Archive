---
title: "Where's my memory?"
date: 2007-06-15
forum: General Help
---

### Post by Erdaron on 2007-06-15
When I run command [FONT="Courier New"]free[/FONT] in terminal, I get this output:
```

             total       used       free     shared    buffers     cached
Mem:       1003264     991112      12152          0      55536     647388
-/+ buffers/cache:     288188     715076
Swap:      2939852      33804    2906048

```

At the moment, the only programs running (aside from system things) are Firefox, XMMS, Thunderbird, SETI@Home, GAIM, and Skype. Not exactly a huge load. Still, how come there are only 12 meg of free RAM?

I'm running Ubuntu 7.04 with 2.6.20-16-generic kernel.

Am I just too much of a noob to understand this?

---

### Post by Citizin on 2007-06-15
now I dont really understand this, but im guessing you have 768MB because of you have around 700MB in cache, and I think when more memory is needed it will be taken out of your cache, just a educated guess though.

---

### Post by vigleik on 2007-06-15
Citizin is right. You're only using about 1/3 of your memory, so you have nothing to worry about. You won't run out.

---

### Post by insane_alien on 2007-06-15
the cache is using nearly all of your unused memory. this is a good thing. the cache just gets wiped when ever the space is needed.

---

### Post by Erdaron on 2007-06-15
Oh, thank you for explaining :).

It certainly didn't feel like it's running low on memory, everything was working smoothly.

---

