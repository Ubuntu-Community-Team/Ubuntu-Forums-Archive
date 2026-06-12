---
title: "Problem with low screen resolution"
date: 2007-06-07
forum: General Help
---

### Post by chris7925 on 2007-06-07
Hi,

I have recently installed Ubuntu 7.04. I am finding it difficult to increase my screen resolution past 1024x768 as no other options are available. How can I increase the resolution?

I have managed to install a ATI restricted driver for the ATI X300 but I am not able to access any of the options available to me in XP

I am completely new to Ubuntu so simple language please.

Chris

---

### Post by dfpd62 on 2007-06-09
Hi Chris

I had a similar problem, and I edited /etc/X11/xorgoconf (as Root) and changed any mention of screen resolution from 640x480 to 1024x768.
you might like to edit yours to whatever resolution you need.
to be safe make a copy (rename) xorg.conf before proceeding.

Hope this helps.

Donald

---

