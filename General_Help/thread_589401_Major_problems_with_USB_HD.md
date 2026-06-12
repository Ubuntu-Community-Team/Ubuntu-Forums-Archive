---
title: "Major problems with USB HD"
date: 2007-10-24
forum: General Help
---

### Post by taggat on 2007-10-24
I recently bought a new 500GB FreeAgent USB HD from Seagate, but it only works intermittently under Ubuntu. Sometimes it shows up, sometimes it doesn't. Sometimes when it does show up and I try to copy something to it or from it, seems to stop taking to it and the counter for how long it's going to take to copy the file grows into infinity by the second, and only a complete forced on/off (holding down the power button until it mechanical shuts down) will make Ubuntu respond again...



My machine is a Dell Inspiron 1501 with Dual Core 2.0Ghz Turion 64bit processors 1GB of ram and a 60GB HD with two partitions one Windows Vista (which is why I tried Linux) and  one Ubuntu 7.04
feisty

The USB HD is split into two partitions one HFS+ without journaling and one ext3.

Help! I would hate for this to be a deal breaker for Linux I think it's been great up till now.

---

### Post by taggat on 2007-10-24
I might have figured it out... still too early to tell but the process that gets frozen is ALSA so working on this hunch I unplugged my USB speakers and was able to transfer over 5.7GB  twice without it freezing on me so my guess is USB audio and USB diskdrives don't live happily in the Ubuntu world just yet.

---

