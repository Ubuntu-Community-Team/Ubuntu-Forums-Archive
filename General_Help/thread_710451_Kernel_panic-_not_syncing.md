---
title: "Kernel panic- not syncing"
date: 2008-02-28
forum: General Help
---

### Post by mario.kostelac on 2008-02-28
So, I have a problem with booting Ubuntu. That doesn't happen always, but sometimes it happens four or five times countiunously.
I get error: "Kernel panic - not syncing: Creation of kmalloc slab kmalloc_dma-512 size=512 failed"...
And.. i did a clean install a few times and.. every time that happend after some period...

Please Help
Btw.. if you need some log or sth like that, just write how to get it and I'll paste it here...

---

### Post by astrotech226 on 2008-02-28
I couldn't say what's causing it, but there are many posts about similar issues when having USB devices plugged in when booting up.  Do you have any?  If so, what happens if you remove them and start up?

Here's a few of the bug reports I found:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/162653]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/162653")
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/130078]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/130078")
[https://bugs.launchpad.net/ubuntu/+source/rt2x00/+bug/135279]("https://bugs.launchpad.net/ubuntu/+source/rt2x00/+bug/135279")

---

### Post by rolandixor on 2008-02-28
I got it too, after stopping the system suddenly during a run of the:confused: (silly mistake) OEM tool:(

Now I can't get it to start!

---

### Post by mario.kostelac on 2008-03-01
I think i found cause of panic... I removed some cheap Genious keyboard and Ubuntu started 10 times correctly... I'll post if it's wrong cause.

Good luck with other panics :)

---

