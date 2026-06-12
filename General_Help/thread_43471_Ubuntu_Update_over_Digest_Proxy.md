---
title: "Ubuntu Update over Digest Proxy"
date: 2005-06-22
forum: General Help
---

### Post by HSukirman on 2005-06-22
Hi,

I installed Ubuntu from CD and my box is behind a squid proxy server that allows digest authentication only.

How can I configure the update applications so that they connect to the update servers? Even apt-get does not work over a digest authentication proxy. (Firefox is working well since it supports that protocol ... I am posting this from my Ubuntu box)

Is there anything I can do? Thank you for looking into this!

Greetings,
HSukirman

---

### Post by HSukirman on 2005-06-22
Sorry for replying to myself ... I found a workaround.

I just changed all references in /etc/apt/sources.list from 'http://blabla..' to 'ftp://blabla..' and the updates are working fine now.

But still ... is there a way to teach apt / aptitude / ubuntu update manager to use the http protocol with digest authentication?

---

### Post by michele.albrigo on 2008-07-08
I'm experiencing the same problems with Ubuntu 8.04 and a digest authenticated proxy. Any suggestion?

---

