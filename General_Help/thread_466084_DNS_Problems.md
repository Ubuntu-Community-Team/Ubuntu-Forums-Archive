---
title: "DNS Problems"
date: 2007-06-06
forum: General Help
---

### Post by jimmydugs on 2007-06-06
I recently removed a few applications through Synaptic (including but not limited to avahi) and also stopped a few services from starting at boot time.  I think I made a mistake somewhere.

I'm now having the problem that addresses aren't resolving correctly.  Firefox seems to not have a problem resolving addresses.  However, if I try to use gaim, ssh, synaptic, I get errors saying that the address cannot be resolved.  It is driving me insane!  Why is firefox able to resolve but no other programs are?

Like I said, I'm sure I uninstalled something I shouldn't have or stopped a service I need.  Can anyone lead me in the right direction?

---

### Post by jimmydugs on 2007-06-06
Issue is resolved.  I removed avahi and had some problems with the nsswitch.conf file.  I believe they have something in common...anyway it works.

I am still curious why firefox was able to resolve addresses but other programs were not?

---

