---
title: "Quick update question: libnspr4-0d?"
date: 2008-07-04
forum: General Help
---

### Post by Culito on 2008-07-04
Hi folks,
I'm getting this message in my update manager lately:

E: /var/cache/apt/archives/libnspr4-0d_4.7.1+1.9-0ubuntu0.8.04.2_i386.deb: trying to overwrite `/usr/lib/libnspr4.so', which is also in package libnspr4

The package libnspr4-0d can't install, So I can't fully update.  Any ideas?

Thanks,
-C

---

### Post by clark3rd on 2008-07-04
I've been getting this too. Doesn't seem serious, but I would like to fix it.

---

### Post by Temujin_12 on 2008-07-05
I can also confirm that I'm getting this too.

EDIT: The following fixed it for me (see [bug report on this issue]("https://bugs.launchpad.net/ubuntu/+source/nspr/+bug/245122")):

```
sudo apt-get remove libnspr4 ; sudo apt-get install libnspr4-0d
```

---

### Post by Culito on 2008-07-05
Cool! That worked for me.  Thanks!

---

### Post by jamaas on 2008-07-06
Me too, thanks!

---

### Post by lukeprentice on 2008-07-09
> **Temujin_12 said:**
> I can also confirm that I'm getting this too.

EDIT: The following fixed it for me (see [bug report on this issue]("https://bugs.launchpad.net/ubuntu/+source/nspr/+bug/245122")):

```
sudo apt-get remove libnspr4 ; sudo apt-get install libnspr4-0d
```
that worked for me, but why was it happening in the first place? there may be many ubuntu users who have no idea about sudo apt-get install etc. the packaging should fixed to make this a smooth install.

---

