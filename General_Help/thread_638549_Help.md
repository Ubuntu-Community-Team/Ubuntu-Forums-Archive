---
title: "Help"
date: 2007-12-12
forum: General Help
---

### Post by jaggy_thistle on 2007-12-12
I tried to use Wubi, and it has totally screwed my laptop (thankfully not my main one). 

When I selected ubunutu after install it kept asking for the CD - after about an hour of this, I decided to abort. Since then, I can't even get windows back - it keeps saying there is an operating system error.

Can anyone help?

---

### Post by ago on 2007-12-12
Run "chkdsk /r" from windows CD or other repair CD you find on the web

---

### Post by jaggy_thistle on 2007-12-12
Thanks.

One other question - If I downloaded the Ubuntu Live CD, could I install it from this state, and just avoid XP?

---

### Post by ago on 2007-12-12
> **jaggy_thistle said:**
> Thanks.

One other question - If I downloaded the Ubuntu Live CD, could I install it from this state, and just avoid XP?

You can install from the live CD even if you have no OS at all on your machine, but be aware that unless you already have a free partition or want to dedicated the full HD to linux, you will need to resize the XP partition and I am not sure how that works when the XP partition is derty (most likely if the operation is unsafe, ntfsresize will refuse to proceed). Hence it would not hurt to run chkdsk anyway.

---

