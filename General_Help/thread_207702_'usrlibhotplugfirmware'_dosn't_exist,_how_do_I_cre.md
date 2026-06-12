---
title: "'/usr/lib/hotplug/firmware/' dosn't exist, how do I create it?"
date: 2006-07-02
forum: General Help
---

### Post by AlexBryan on 2006-07-02
I'm following some instructions on how to install ipw2200 drivers and I've come to a point where drivers need to be put into this directory i think, but it dosn't exist. Should I create it? and if so how, I kep getting permission denied errors with mkdir.

---

### Post by mlind on 2006-07-02
Hotplug has been deprecated by udev. And modprobe has now hotplug's blacklisting feature.

What do the instructions say about hotplug part?

---

### Post by vigleik on 2006-07-02
I have my firmware in /lib/firmware/. It's for a completely different piece of hardware, but I think all firmware goes there with udev.

Vigleik

---

