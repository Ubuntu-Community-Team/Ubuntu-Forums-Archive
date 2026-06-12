---
title: "Should Speech Dispatcher have /bin/sh as a shell?"
date: 2015-03-29
forum: General Help
---

### Post by chopra on 2015-03-29
It was my understanding that system accounts generally had either /bin/false or /usr/sbin/nologin as their shells for security reasons.  I noticed that in Ubuntu 14, all of the system accounts that had the sh shell in 12 got changed to /usr/sbin/nologin.
Except libuuid, which has no shell in the passwd file, and so defaults to /bin/sh.

Then, there's speech dispatcher, which, on my system, still has /bin/sh as its shell.  First, is this a security issue? Second, is it intentional, or did someone just forget to change it?
 I don't understand why some system accounts had /bin/false from the start while others started with /bin/sh and were changed to /usr/sbin/nologin.

Chopra

---

### Post by slickymaster on 2015-03-29
> **chopra said:**
> It was my understanding that system accounts generally had either /bin/false or /usr/sbin/nologin as their shells for security reasons.  I noticed that in Ubuntu 14, all of the system accounts that had the sh shell in 12 got changed to /usr/sbin/nologin.
Except libuuid, which has no shell in the passwd file, and so defaults to /bin/sh.

Then, there's speech dispatcher, which, on my system, still has /bin/sh as its shell.  First, is this a security issue? Second, is it intentional, or did someone just forget to change it?
 I don't understand why some system accounts had /bin/false from the start while others started with /bin/sh and were changed to /usr/sbin/nologin.

Chopra
Yes, you're right. It's a security issue, that's is being taken care off. See [bug 1319970]("https://bugs.launchpad.net/ubuntu/+source/speech-dispatcher/+bug/1319970")

---

