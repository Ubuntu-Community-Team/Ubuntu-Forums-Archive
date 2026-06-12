---
title: "Which easy-to-configure SIP server for 12.04 LTS?"
date: 2015-01-02
forum: General Help
---

### Post by Elmi77 on 2015-01-02
Hi,

I'm planning to install a SIP-server on my Ubuntu 12.04 LTS which also supports TLS/encryption. I already tried Asterisk but it's configuration is a mess, dozens of huge and strange configuration files and even creating a simple user account requires at least two of them to be changed. And no Webmin module exists for it.

So my question: is there an workign alternative available for Asterisk which encrypts payload and not configuration files? Mans a server that can be handled more easy?

Thanks!

---

### Post by TheFu on 2015-01-02
Most businesses running asterisk deploy onto dedicated hardware and use something like FreePBX or Elastix as a quick-start to a working system.  At my local asterisk group, nobody seems to deploy a general purpose distro, then add a PBX.  These distros have a web front-end.

I've tried doing this with freeswitch, got it working but maintenance was just too hard. Much easier to use a complete HW swap (only about $150) so that the old version can be put back quickly if something isn't correct, at least for a small office.

---

