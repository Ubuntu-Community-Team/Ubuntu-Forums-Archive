---
title: "USB safety on 16.04 - USBguard from 16.10 version, or dev's github tarball?"
date: 2017-11-09
forum: General Help
---

### Post by donsevilla on 2017-11-09
Hi all


I've been chasing ways of dealing with USB drives more 'hygenically' (isolation, establish trust, etc). I came across [USBguard]("https://dkopecek.github.io/usbguard/"), a software package that facilitates a black/whitelist policy for USB ports and devices. I want this.

USBguard has its own download on github.

I'd be more comfortable with a repository-style, compatible, auto-updatable, managed by my system. 

USBguard is available from 16.10 onwards; there are no xenial backports. Debian seems to have its own. 

What is best course of action, in a case like this? 

1. install from the 16.10 package? Putting aside "how?", is that viable, anyway?

2. Sit tight and wait til something is backported? I flat-out don't have the skills to test or backport myself, especially for something security related.  Is there a protocol to ask?

(I'd really prefer not to sys. upgrade). 

Or, 

3. install from the github tarball, and manually keep an eye on that github page. Is there a more systematic/automatic way to watch for updated versions? (Unless I have misunderstood this altogether and a package installs an update tool that hooks into e.g. apt update, as standard?)

Thanks 

B.

---

