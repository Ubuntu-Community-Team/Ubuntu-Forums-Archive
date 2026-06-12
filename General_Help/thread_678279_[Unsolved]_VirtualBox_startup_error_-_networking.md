---
title: "[Unsolved] VirtualBox startup error - networking"
date: 2008-01-25
forum: General Help
---

### Post by cdaringe on 2008-01-25
Hey everyone,
hopefully this will be a quick and easy one to nail
When i boot up virtualbox and begin to load my virtual machine i get this error

VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).

ive already narrowed it down to networking.  it has something to do w/ the networking parameters. everything boots up fine when i have NAT enabled.  but when i setup the  host interface i receive that error.
I already fixed the tun file's access rights. But interestingly enough when i setup the exact same virtualbox as ROOT, it boots perfectly.  so im guessing that the host interface is trying to access something that i cannot...
googled, no results. any takers?

---

