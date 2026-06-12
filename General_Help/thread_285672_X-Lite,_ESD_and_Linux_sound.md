---
title: "X-Lite, ESD and Linux sound"
date: 2006-10-27
forum: General Help
---

### Post by sog on 2006-10-27
I recently installed Asterisk on a local machine and was looking around for a softphone to use (Ekiga's unusably slow for me - see the bug here [https://launchpad.net/bugs/67652)](https://launchpad.net/bugs/67652)). Eventually, I turned up X-Lite, which I'm not a huge fan of visually but works. 

Sometimes, anyway. Basically, X-Lite works as if there is no sound switching whatsoever. When the machine is booted fresh, it works just fine. As soon as another application grabs sound, however - like Firefox or VLC - it stops working and kicks out an error saying:

> Warning: /dev/dsp appears to be a valid audio device, but I cannot
         open it.  Please ensure that no other applications are
         using the audio device (perhaps by trying ``lsof /dev/dsp'').


Looking around for a solution, I've seen recommendations to kill ESD. But then I wonder why it's enabled by default? And whether or not it's the solution to the problems I had while still on Dapper (I'm on Edgy now) where all applications behaved this way, not just X-Lite?

Basically my question is: what's the ideal configuration for having multiple applications share access to sound with no issues?

Any help gratefully accepted.

---

### Post by qphrenqp on 2007-07-16
Hello!

this is what I made today to make X-Lite work everytime (with kubuntu feisty fawn) and even sound mixing with other softs:

```

sudo apt-get install alsa-oss
```

and then launch xlite like this :

```

aoss xtensoftphone
```

---

