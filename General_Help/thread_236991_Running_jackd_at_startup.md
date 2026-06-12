---
title: "Running jackd at startup"
date: 2006-08-15
forum: General Help
---

### Post by kernco on 2006-08-15
Hi,

I'd like to run jackd at startup.  How would I set this up?  I tried adding it under System->Preferences->Sessions, but it didn't start.  

Also, with jackd running is there a reason to have esd running?

Thanks.

---

### Post by drycellbattery on 2006-08-15
Jack won't run when esd is running. You will have to manually disable esd in the preferences -> sound . I know that in qjackctl you can pass instructions to kill the aRts sound server when you start jack, but I don't know if it would work with esd. You could try it.

I'm not sure how to get jack to start when log in. Maybe esd was the problem. Go check out the Ubuntu Studio section in the forum as well, there's lots of discussion about jack, a realtime kernel, ardour, etc. there.

---

