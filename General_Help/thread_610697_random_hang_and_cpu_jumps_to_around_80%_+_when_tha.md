---
title: "random hang and cpu jumps to around 80% + when that happens"
date: 2007-11-12
forum: General Help
---

### Post by ultimatsz on 2007-11-12
i am not sure if the cpu jumps to 80% or more.. because when the system is locked.. the windows turned grey / black and white and every window failed... music stop playing.. even system monitor turned grey.

after finished.. the cpu is around80% for no reason...

what could be the reason? has it got to do with nvidia driver?

or is it because i m using duo core processor?

intel core 2 duo processor t5600
(1.83Ghz,667Mhz FSB, 2mb l2cache)
nvidia geforce go 7300 
1Gb ddr2

---

### Post by os.getlogin on 2007-11-12
So, I'm not sure that I fully understand.  Are you saying that everything locks up?  Does it "unhang" by itself or how do you get out of it?

Some things to answer:
1. dmesg | tail
2. are you running compiz and effects?
3. what apps are you running at the time of hang-up?
4. are you using the proprietary nvidia driver?

---

### Post by ultimatsz on 2007-11-12
whats 1?

yes i m running compiz... when it hangs compiz works partially

it really does not matter what programs i m running. it happens with all application windows. it hangs for like 10seconds and unhang it self... randomly

it is like when i m doing something.. suddenly the windows will become greyed out. everything becomes locked.. thou compiz still works... for 10seconds..  then it returns to normal again. when it gets locked music stops playing. after recovering the music skips to that much amount of time.

i m using 100.14.23 driver nvidia.

---

### Post by os.getlogin on 2007-11-12
```
dmesg | tail
```
gives you the tail end of some system messages.  This is often a first step in attempting to figure out what's wrong.  Type it into a terminal.

I'd bet that it's a compiz problem.  Try shutting it off to see if you still get the hangs.  My compiz won't stay running (using nvidia's driver on the geforce 8500).

Not sure how to debug compiz.

Good luck!

---

