---
title: "Hourly updates"
date: 2008-07-09
forum: General Help
---

### Post by bloodorange on 2008-07-09
Hi All

Does anyone know if it's possible to configure the 'Check for updates:' drop down (in the Software Sources dialogue) to have an 'Hourly' option.  I'm pretty sure Fedora 9 can check for updates hourly, and I'd like to be able to do the same.

Thanks.

---

### Post by justleen on 2008-07-09
you could add an entry in root's cron, something like ```

apt-get update -qy

```
-q = quiet
-y = assume yes, answers yes on all questions

---

### Post by bloodorange on 2008-07-11
Thanks very much for that; I'll give it a go.

Cheers

---

### Post by Bakon Jarser on 2008-07-11
You really need your computer updated every hour?  I think it's kind of rude to be using their bandwidth to check for updates that often.  I don't think they release updates more than once a day anyways.

---

### Post by bloodorange on 2008-07-15
I just don't like missing important security updates.  What if the update's released late in the day, after an automatic update check has been actioned?

I do manual update checks a few times a day anyway, I don't think you should call me rude just because I want my system security kept up to date.  I wouldn't have thought it takes up that much bandwith anyway.

---

### Post by brian_p on 2008-07-15
> **bloodorange said:**
> I just don't like missing important security updates.  What if the update's released late in the day, after an automatic update check has been actioned?

Mirrors tend to synchronise at a set time each day so checking frequently after they have updated is pointless.

---

### Post by bloodorange on 2008-07-16
Thanks for your negativity Bakon Jarser and brian_p.  I didn't need anyone's opinion on whether or not I should 'want' hourly updates, just if it's possible and, if it is, how you do it.

Forget it...!

---

