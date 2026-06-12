---
title: "Two Quick Questions"
date: 2008-02-12
forum: General Help
---

### Post by nabl on 2008-02-12
I just did a fresh install of Ubuntu last night (I had an older Kubuntu installation previously), and almost everything is looking good. However, I have noticed two things that I would like to fix/change.

First, I would like to set my Windows partitions to mount as read-only. I read a thread on how to do this a while ago, but I could not find it, even after various searches. I believe I just need to edit /etc/fstab, but I'm not sure what to change/add.

Second, my CD drive indicator light is on constantly from the time I turn on my computer. I can do a quick fix by opening it and closing it (after that, it functions correctly until the next restart), but I would rather have a permanent fix for this problem. And it works under Windows, so it isn't a hardware problem; I think it has something to do with the drivers.

I highly appreciate your help! Thanks in advance!

---

### Post by apetresc on 2008-02-12
To answer your first question, it should just be enough to add the 'ro' option to the options list of the corresponding /etc/fstab entry for your Windows partition.

---

### Post by nabl on 2008-02-12
> **AdrianP said:**
> To answer your first question, it should just be enough to add the 'ro' option to the options list of the corresponding /etc/fstab entry for your Windows partition.That was easy enough. :) Thanks!

---

