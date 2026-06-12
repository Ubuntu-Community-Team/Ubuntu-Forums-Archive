---
title: "How do you shut down acpid"
date: 2006-08-31
forum: General Help
---

### Post by jsmidt on 2006-08-31
I am trying to get suspend to work and was told this:


 But the usual (all Toshibas do this
AFAIK) power-button event after resume is not ignored by your userspace.
Try integrating s2ram into your acpid configuration or just shut acpid down
before suspend to verify this.  Try the s2ram combinations from "init=/bin/bash" to find out which ones
work.


Anyways, how do shut down acpid?  Also what is this "init=/bin/bash" stuff?  Thanks.

---

