---
title: "Lockup! python invoked oom-killer"
date: 2008-06-13
forum: General Help
---

### Post by doubleyousee on 2008-06-13
Ok, long time lurker, first time poster :oops:

Alright, in the last few days, Ubuntu has locked up pretty badly on me, the first few times it was just incredibly slow and clearly running out of memory. Couldn't login to tty1, it would timeout before requesting my password, I was forced to look up how to take the system down "softly?" I gathered from a forum post something about Alt-Sysreq R-E-I-S-U-B, I recall vaguely what all that was for, but either way, no luck. I was eventually forced to either Ctrl-Alt-Del or in the case of yesterday, hard reset.

At first I thought it was an issue with the Firefox3-RC2 I had forced on from an outside repository because I am just too imaptient, but I removed that and went to the ubu repository version (which is RC3? by now...) and low and behold same problem but worse this afternoon!

I came home to a full lockup, no video output, no response to anything on the keyboard. I could ping from my other machine but no SSH (no rejection though, just a hang on a blank screen from puTTY) and no VNC.

I did a little log digging, I can see what time things went awry. There was a oom-killer invocation by python suddenly while no-one was home, so I hypothesize that something is leaking memory.

I will post the relevant logs for someone with a little more experience with this stuff to interpret, but I'm not 100% sure what is relevant.

Any help would be appreciated :)

Cheers!

---

