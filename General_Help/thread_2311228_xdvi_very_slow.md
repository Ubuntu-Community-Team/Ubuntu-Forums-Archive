---
title: "xdvi very slow"
date: 2016-01-25
forum: General Help
---

### Post by phorminx on 2016-01-25
I am using ubuntu 14.04 on several computers (similar hardware, similar installation).  I am confused that on one of them xdvi runs very slow, requiring like 15s to completely display a page.  Lines are displayed one by one as if xdvi was running on a remote host via a slow network connection, but this really happens locally. I can't tell when this started. I had to re-install this computer a while ago. Maybe I did not use latex on this computer since then and only now I notice this problem, though maybe it has existed for some time.

I do not know how evince displays dvi files.  (Does it use the same or a different display engine as xdvi?)  Evince displays my dvi files instantly, as expected. But evince does not provide the magnifying lens of xdvi, so it is no replacement for me.

Is it possible to have a misconfigured font cache or something of that kind (though I have no clue what might have triggered this)?

---

### Post by gtmarks on 2016-09-04
Does it help if you run xdvi with the -copy flag?

---

