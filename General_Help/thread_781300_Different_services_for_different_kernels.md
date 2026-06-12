---
title: "Different services for different kernels"
date: 2008-05-04
forum: General Help
---

### Post by junglebarry on 2008-05-04
Is is possible to get different kernels to start different sets of services?

For example, I would like to run 2 configurations on my laptop:
[1] everyday use, with lots of services (e.g. kdm, apache, networking, anti-virus, firewall, SSH) installed and running, using a generic kernel
[2] realtime use for audio recording, running a bare minimum of services (gdm, no network, for security) and in a realtime kernel.

(I need gdm for Ardour, which seems to perform worse under kdm.)

I would like to be able to configure this so that I simply select either "generic" or "realtime" in GRUB, and get my desired service level.

I had a look at run-levels and init scripts, but these seem to be for something subtly different. (Perhaps I have misunderstood?)

I have also found a little information on something called SCPM:

[http://forge.novell.com/modules/xfmod/project/?scpm](http://forge.novell.com/modules/xfmod/project/?scpm)

This seems to do what I want, but is not part of Ubuntu...

---

