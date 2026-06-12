---
title: "Lots of processes running grep -E -l ^[0-5]  /dev/.bootchart/* eating up CPU big time"
date: 2016-05-04
forum: General Help
---

### Post by Slarty Bardfast on 2016-05-04
Hello,

I recently upgraded my machines to 16.04.  For some reason, now one of them (at least the only 1 I've noticed so far) seems to slow to a crawl quite often.  When I run top, I'm shown that there's usually several processes of grep running and using up at least 40% CPU, sometimes tapped out to 100%.

top -c shows me things like grep -E -l ^[0-5]  /dev/.bootchart/proc/blah blah and then a pagemap file.  I also saw it running on /dev/.bootchart/proc/kcore one time.

It seems when it starts it's scanning glance-api and glance-registry so I thought maybe that had something to do with it, but then it started going through other files.  

If I kill these they just respawn.  Rebooting seems to work for a bit and then they return.  I don't see anything in cron that indicates a task running for this.  

Is this normal?  It almost seems like a prank, it's just going through these huge files and looking for numbers beginning with 0 to 5.  Should I be concerned, is there a way to stop it from happening, or less, or at least renice it?

Also, if this is normal behaviour, can someone please give me a brief overview of what is going on here or provide some documentation if it's a pain to explain?  So far I can't really find anything or at least I'm not sure where to start looking.

Thanks!

---

### Post by vasa1 on 2016-05-04
Do you really need to have *bootchart* installed?

---

### Post by Slarty Bardfast on 2016-05-05
Thanks for your reply vasa1!  Is that what could be doing this?  I have no recollection of installing bootchart!  I must have installed it at some point to monitor a boot (or shutdown?) issue I was having or something like that.  I never noticed it before the upgrade though.  It's not something that's added with 16.04 then?  Totally safe to get rid of?

---

### Post by vasa1 on 2016-05-05
> **Slarty Bardfast said:**
> ... It's not something that's added with 16.04 then?  Totally safe to get rid of?I'm nearly certain it isn't part of a default installation in 16.04. Yes, it is something you can uninstall. You can confirm whether it is installed with *apt-cache policy bootchart*.

---

### Post by Slarty Bardfast on 2016-05-05
Yes, sure enough, it was installed.  I've removed it and I'll keep an eye out.  Thank you again!

---

