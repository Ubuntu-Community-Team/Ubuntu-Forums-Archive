---
title: "Trouble with Update to Firefox 40"
date: 2015-08-19
forum: General Help
---

### Post by dschaller on 2015-08-19
I updated to Firefox 40 this morning, and the new version is essentially unusable to me. It takes 15+ seconds to switch between tabs. Screen repainting is done incorrectly or not at all. I've never experienced Firefox so sluggish. Running Ubuntu 12.04. Is anyone else being affected this way?

---

### Post by dschaller on 2015-08-19
I've tried both refreshing Firefox and starting it in safe mode and neither helps.

---

### Post by dschaller on 2015-08-19
So I purged Firefox 40 and installed 39.0.3 again (still had the old package in the cache). Things went back to normal. So I'm definitely having a problem going from 39 to 40. I've never seen the sort of screen refresh problems that I suddenly saw after this update.

---

### Post by Topsiho on 2015-08-20
See the thread > 14.04 Firefox not operational after update
Maybe it is the same problem, only you are more patient than other people, waiting 15+ seconds. Or problem is related.
Anyway, the update to FF40 for some of us has undesirable results.

I received a new update of FF today, maybe this solves the problem. Did not try this yet, as I now work on an other computer.

Topsiho

---

### Post by thomas-delhomenie on 2015-08-25
Same problem here about screen repainting. Firefox 40 is unsable. Almost each time I go to another page, I have to switch to another application, then to switch back to firefox to make it display correctly.

---

### Post by johna2 on 2015-08-26
I'm having the exact same problem with Firefox 40.0.2 on Ubuntu 12.04.05, even in safe mode, even with a brand-new fresh profile.  

I reverted to Firefox 39 and the issue went away.

I filed bug [https://bugzilla.mozilla.org/show_bug.cgi?id=1198875](https://bugzilla.mozilla.org/show_bug.cgi?id=1198875) about this.

---

### Post by monkeybrain20122 on 2015-08-26
Probably because OMTC (off main thread compositing) is enabled by default in FF40 and some hardware (gpu) is not behaving as expected. In URL bar type about:config, then set layers.offmainthreadcompoistion.enabled to be false and restart Firefox. See if that solves your problem.

---

### Post by dschaller on 2015-08-27
> **monkeybrain20122 said:**
> Probably because OMTC (off main thread compositing) is enabled by default in FF40 and some hardware (gpu) is not behaving as expected. In URL bar type about:config, then set layers.offmainthreadcompoistion.enabled to be false and restart Firefox. See if that solves your problem.

Nice tip! This does seem to get at the problem. For me, disabling OMTC made Firefox usable again. Thanks, I never would have stumbled on this myself.

---

### Post by johna2 on 2015-08-27
It worked!  Thank you monkeybrain20122!

---

### Post by thomas-delhomenie on 2015-10-15
Works fine for me too, thanks a lot !!

---

