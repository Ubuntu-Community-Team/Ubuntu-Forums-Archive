---
title: "How to tell if TRIM is enabled in 14.04?"
date: 2014-04-06
forum: General Help
---

### Post by mark2741 on 2014-04-06
Just did a clean install of 14.04 on a new SSD. 

I have read that 14.04 is supposed have TRIM enabled by default, and that it is important. Since 14.04 has not been released yet, I was wondering if there was a way to verify that TRIM is enabled? I'd be surprised if it wasn't, but just in case I'd like to verify.

---

### Post by SuperFreak on 2014-04-06
[https://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking]("https://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking")

---

### Post by mark2741 on 2014-04-06
Thanks. Based on that site's recommended test, Ubuntu 14.04 did not enable TRIM by default for my SSD. I went ahead and followed the instructions for scheduling TRIM via cron, per the recommended method.
I'm using a brand new Intel 335 240GB SSD.

---

### Post by frostschutz on 2014-04-06
[http://unix.stackexchange.com/a/85880/30851](http://unix.stackexchange.com/a/85880/30851)

---

### Post by mark2741 on 2014-04-06
Numerous testing methods aside, it does concern me that 14.04 does not have TRIM enabled by default.

---

