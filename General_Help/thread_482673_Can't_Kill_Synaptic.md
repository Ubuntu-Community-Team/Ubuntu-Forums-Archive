---
title: "Can't Kill Synaptic"
date: 2007-06-23
forum: General Help
---

### Post by init1 on 2007-06-23
I can't kill synaptic with ```
kill 4777
``` or ```
killall synaptic
```
Every time I do, ps -A tells me that synaptic is still running under 4777

---

### Post by Maxtorm on 2007-06-23
How about ```
kill -9 4777
```

---

### Post by init1 on 2007-06-23
What does the -9 do? It's not an issue anymore, a restart fixed it, but if it happens again, I will know to try it.

---

### Post by Maxtorm on 2007-06-24
Heh.  Knew you were going to ask that.  Frankly, I can't remember.  Just seem to recall way back in my Unix days that someone said "kill -9" was the be all and end all of kill commands. :)

---

### Post by Qu4k3R on 2007-06-24
I would use:
> 
ps -e

To see the ID's
Then
> 
kill -kill <victim_ID>

The "-kill" option is like the "-9" option I think so.
you can read about it on the man pages.

---

### Post by init1 on 2007-06-26
I found that using xkill and/or kill -9 usually works for this sort of thing.

---

### Post by ryanVickers on 2007-06-27
They usually kill ok, WAY better than windows, but it's not perfect.  For instance, well, not really, but :) my computer has been totally locking up randomly lately, and it's not just linux, but the bios and all that too!?!

---

### Post by AlexThomson_NZ on 2007-06-27
Think of "kill 1234" as asking nicely and "kill -9 1234" as telling it to close OR ELSE!!! :)

I'd be a bit cautious about killing synaptic if it's in the middle of something tho...

---

### Post by Qu4k3R on 2007-06-28
you can use also > sudo killall -9 synaptic

---

