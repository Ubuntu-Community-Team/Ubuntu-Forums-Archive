---
title: "Need help with logrotate &amp; anacron"
date: 2008-03-07
forum: General Help
---

### Post by pearjam on 2008-03-07
Hi!

I'm looking into how to manage logs with logrotate & anacron. I'd like to learn how to use (configure) them, but the info I've found doesn't explain how. I'm not good with man pages, so I figured I'd ask here. Maybe someone knows of a link I've missed that explains it all?

(Ubuntu Studio 8.04 Alpha 6 64 bit - I checked Synaptic, and both logrotate and anacron are already installed.)

Thanks for any help!

---

### Post by dcstar on 2008-03-07
> **pearjam said:**
> Hi!

I'm looking into how to manage logs with logrotate & anacron. I'd like to learn how to use (configure) them, but the info I've found doesn't explain how. I'm not good with man pages, so I figured I'd ask here. Maybe someone knows of a link I've missed that explains it all?

(Ubuntu Studio 8.04 Alpha 6 64 bit - I checked Synaptic, and both logrotate and anacron are already installed.)

Thanks for any help!

/etc/logrotate.d contains all the profiles for the package log files that logrotate will work on. /etc/logrotate.conf holds the basic configuration.

You do not need to touch anacron, it will run logrotate when it is supposed to.

---

