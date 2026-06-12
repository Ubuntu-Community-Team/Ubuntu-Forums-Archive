---
title: "Firefox crashes"
date: 2008-02-25
forum: General Help
---

### Post by vital101 on 2008-02-25
Hey everyone,

I have recently ran into problems with firefox crashing on me.  Everytime I navigate away from my homepage, it instantly crashes.  When it exits I get "Core Dumped" and that's it.  I also tried launching in safe-mode, disabling everything, and it still crashes.  Any ideas?  Or can someone point me to the crash logs for firefox on Ubuntu?

---

### Post by vital101 on 2008-02-26
Just wanted to update the situation a bit.

I was cruising the forums a bit and found a few possible solutions, but none of them worked.  One of them was to clean up my fonts, so I ran the following code:
```

dpkg-reconfigure libcairo2 libpango1.0-common
fc-cache -fs
update-pangox-aliases

```

That failed to work.  The other option I tried was downgrading flash, that also failed.  Firefox still crashes when I click a link, open a bookmark, or go to a page using the address bar.

Help!  I miss my firefox!

---

