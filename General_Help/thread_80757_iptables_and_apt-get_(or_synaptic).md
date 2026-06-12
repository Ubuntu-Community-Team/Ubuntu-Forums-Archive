---
title: "iptables and apt-get (or synaptic)"
date: 2005-10-22
forum: General Help
---

### Post by wgscott on 2005-10-22
I'm more used to ipfw and don't know anything really about iptables (and am comparatively new to linux).

I installed KMyFirewall which appears to be a reasonably idiot-friendly gui for iptables -- at least it explained things well enough that I could figure out what was going on.  All my incoming and outgoing services (NFS, ssh, web and so forth) are behaving fine.  So far, less hassle than ipfw on OS X (which I am more familiar with).  But I just recently noticed that I managed to block whatever ports are involved with apt-get.  If I deactivate the firewall, apt-get works, so I know that is the problem.  But I'd like to be able to figure out what rule(s) I need to incorporate for iptables so that I can use apt-get (and synaptic) without having to suspend the firewall.

I realize this is a RTFM question, but I find it impenetrable, and surely this must come up a lot.

Many thanks in advance!

---

### Post by adwait on 2005-10-22
Apt-get uses wither wget or ftp to download, so I think opening port 21 for outgoing connections should do it.

---

