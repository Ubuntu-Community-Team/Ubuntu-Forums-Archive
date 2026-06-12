---
title: "What makes Ubuntu's Vino working with Mac but not Vino of another Linux?"
date: 2020-05-09
forum: General Help
---

### Post by Gvarelov on 2020-05-09
Hi,
Not sure where would this thread go so I am posting it in General Help.
I have a dual boot machine, old laptop with both Ubuntu 20.04 and RHEL 8.1 on it. I am accessing that laptop via my Mac's Screen Sharing. With Ubuntu, it works like a charm. With RHEL 8, Mac's screen sharing throws an error about incompatibility. Although both distros seem to use the same Screen Sharing software that you could set from GUI- it's Vino if not mistaken.
So what is different with Vino in Ubuntu that connection works than Vino in RHEL 8? In Ubuntu, Vino will remember your password that you set for screen sharing, in RHEL it instantly forgets it.
What made Ubuntu's Vino work with Mac?
Note that I already went down the route of installing TigerVNC server in RHEL 8 and performed its configuration with the result being the same incompatibility error thrown by Mac's Screen Sharing application.

---

### Post by HermanAB on 2020-05-09
Hmm, VNC is an excellent way to get your computer hacked.

Rather use SSH.  It is secure and more capable than VNC.

---

### Post by Gvarelov on 2020-05-09
> **HermanAB said:**
> Hmm, VNC is an excellent way to get your computer hacked.

Rather use SSH.  It is secure and more capable than VNC.
Did you read the title? Did you read the question? Do you think your answer is even remotely helpful? Have you tried not writing back anything if you don't know the answer?):P

---

### Post by HermanAB on 2020-05-09
Uhm, you do realize that Vino == VNC don't you?

---

