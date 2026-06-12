---
title: "Universe &quot;cannot be authenticated&quot;!"
date: 2007-04-23
forum: General Help
---

### Post by pikkio on 2007-04-23
I've just upgraded my ubuntu box from Edgy to Feisty (I made a CD installation, after I had formatted my HD).
Anyway, now I'm "unable" to install new packages from the universe repository. For example, while trying to install the gaim-guifications package:

> WARNING: The following packages cannot be authenticated!
  gaim-guifications
Install these packages without verification [y/N]? 
E: Some packages could not be authenticated

Of course I can easily say "Yes", but I want to install software only from trusted sources. So, where can I find the Universe gpg key for Feisty? And, more important, why wasn't it installed out-of-the-box?

Thanks

---

### Post by tgm4883 on 2007-04-23
Wait, did you upgrade or do a fresh install?

Also, post your /etc/apt/sources.list

---

### Post by zvacet on 2007-04-23
Try with 

```
sudo aptitude update && sudo aptitude upgrade
```

and send your source list if no luck

---

### Post by pikkio on 2007-04-23
It was a false alarm, now it works all fine. I think it was only a mirror temporary problem.
Thank you all, anyway :)

---

