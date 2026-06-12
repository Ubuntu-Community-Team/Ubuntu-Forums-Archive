---
title: "firefox 2.0.0.5 segfault"
date: 2007-07-24
forum: General Help
---

### Post by suoko on 2007-07-24
Hi,

firefox 2.0.0.5 is segfaulting very often.
I only have the google desktop and the delicious extensions installed.

I'm now using swiftfox which is working ok

any solution?

---

### Post by Seisen on 2007-07-24
Trying running firefox in safemode and see if its still segfaulting.

---

### Post by benx009 on 2007-07-24
> **suoko said:**
> Hi,

firefox 2.0.0.5 is segfaulting very often.
I only have the google desktop and the delicious extensions installed.

I'm now using swiftfox which is working ok

any solution?

maybe reinstalling firefox would help?

---

### Post by suoko on 2007-07-25
in safe mode it seems working ok.
I noticed that google desktop has installed an extension for firefox. 
that could be my  problem. How can I remove it without removing google desktop?

found this bug report: [https://bugs.launchpad.net/ubuntu/+source/mozilla-firefox/+bug/124140](https://bugs.launchpad.net/ubuntu/+source/mozilla-firefox/+bug/124140)

I'm now trying with the gdl extension disabled

---

### Post by suoko on 2007-07-25
I can confirm the problem was the gdl extension.
With it disabled firefox is working perfectly again

---

### Post by Seisen on 2007-07-25
See sometimes the extensions can cause problems.

---

