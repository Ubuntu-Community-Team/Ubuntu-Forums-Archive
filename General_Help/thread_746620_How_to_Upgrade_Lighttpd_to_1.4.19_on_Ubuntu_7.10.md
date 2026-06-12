---
title: "How to Upgrade Lighttpd to 1.4.19 on Ubuntu 7.10?"
date: 2008-04-05
forum: General Help
---

### Post by jpmd on 2008-04-05
Background:

I'm a Linux newbie, but for the last six weeks have been very happy with Ubuntu, my first Linux experience.

Configuration:

Ubuntu 7.10 running on 10-year-old Gateway G6-450 with 256 MB of RAM.  No terminal or keyboard is installed--I do everything with SSH using PuTTY.

*System runs beautifully.*

I swapped out Apache2 with Lighttpd version 1.4.18.

*System runs beautifully.*

I even loaded IBM Lotus Domino Server 7.0.2 on the box, using a different port because Lighttpd is port 80 for now.

*System runs beautifully.*

**I recently saw that Lighttpd.net recommends upgrading to version 1.4.19.**

I tried the apt-get update / upgrade / force-update approach, but it appeared to think that version 1.4.18 listed as the current version.

I explored the Lighttpd forums, documentation, and general site, but can't seem to figure out how to upgrade my version of Lighttpd.  I found a deb distribution package after getting referred to: [http://packages.debian.org/etch-backports/lighttpd](http://packages.debian.org/etch-backports/lighttpd).

*Did I mention that I'm a Linux newbie?*

**How do I update my version of Lighttpd with Ubuntu? ** 

Naturally I'll want the update to preserve my existing configuration settings.

I tried to find an answer in this forum as well, using 'lighttpd' as a search keyword, but maybe I missed it somehow.  If it's already posted somewhere, feel free to send me a link.

Thanks for your help!

John

---

### Post by jpmd on 2008-04-05
By the way, before trying to upgrade, I thought I would figure out what my current version was.

I rummaged about the forums (forii?) and documentation and wikis, but couldn't figure it out.  It was only by accident that I stumbled on this command:

**lighttpd -version**

So, for other newbies out there, keep this command in your back pocket.

Keywords:  upgrade, update, version, get current version, lighttpd, lighty

---

