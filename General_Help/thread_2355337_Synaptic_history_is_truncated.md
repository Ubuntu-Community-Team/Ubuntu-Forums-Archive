---
title: "Synaptic history is truncated"
date: 2017-03-11
forum: General Help
---

### Post by PaulBx on 2017-03-11
$ uname -a
Linux len780 4.4.0-66-generic #87-Ubuntu SMP Fri Mar 3 15:29:05 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
16.04 LTS

I was trying out browsers, installing and removing them. Today (3/11) I installed Midori and removed it, installed Chromium and removed it. The history simply missed the Midori action and just caught the end of the Chromium removal. Those other two entries for today, on the left, are for subsequent actions, when I was trying epiphany. If you look in dpkg.log the information about Midori is there.

[IMG]http://img.photobucket.com/albums/v63/Zxcv12003/Screenshot%20from%202017-03-11%2013-41-43_zpsluvq7buh.png[/IMG]

---

### Post by PaulBx on 2017-03-11
Never mind, I found this bug: [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/743498](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/743498)

---

