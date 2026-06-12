---
title: "Time synhronization"
date: 2007-11-27
forum: General Help
---

### Post by Alex Dinamo on 2007-11-27
Since I upgraded to Gutsy, the moment I boot my machine and log in, the time is wrong. I've always used "time and date settings" control panel to keep my machine synchronized with time servers and it is not working now. To fix this, first thing I do every day is enter the aforementioned control panel and just "touch something" on the "select servers" list, just add or remove one more server than needed. If I do that, time is immediately fixed.

What do you think?

Alex

---

### Post by TidusBlade on 2007-11-27
I had that problem, I just manually synced and left it until it became wrong, so I would synci t again manually. It was maybe once a week... so not a big pain.  Since you say every time you boot, I would stick with your method, unless you actually want it to work, then maybe try to sync it to local servers?

---

### Post by Alex Dinamo on 2007-11-27
Maybe I was not clear enough. I am not talking about the clock drifting (like little by little). I am talking about a BIG difference of hours, like it was on a different timezone or something.

BTW: If I execute by hand the command "ntpdate", which I think is involved in this process of setting the date, I get the following error:

```
27 Nov 13:50:12 ntpdate[18410]: no servers can be used, exiting
```

... which is strange since, as I already said, I CAN sync by manually modifying the server list...

Alex

---

