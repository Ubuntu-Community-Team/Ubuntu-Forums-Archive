---
title: "apt-get and synaptic broken"
date: 2007-07-07
forum: General Help
---

### Post by pref-at-laval on 2007-07-07
I've been using 6.06LTS for a while now and all of a suden I can't install packages anymore. When I use Synaptic or apt-get in a console I always get the same error message for whatever the package I'm trying to install:
E: Sub-process /usr/bin/dpkg received a segmentation fault.
Can anyone help?

---

### Post by Immolatus on 2007-07-07
maybe try:

sudo apt-get install -f

---

### Post by Immolatus on 2007-07-07
sorry, in a terminal.

---

### Post by pref-at-laval on 2007-07-11
tried "sudo apt-get install -f"
It runs smoothly but it still doesn't fix the problem.

Thanks anyway.

---

