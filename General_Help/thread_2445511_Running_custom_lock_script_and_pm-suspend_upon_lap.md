---
title: "Running custom lock script and pm-suspend upon laptop lid closure"
date: 2020-06-15
forum: General Help
---

### Post by petersanchez on 2020-06-15
Hey All. I'm running 18.04 on a X1C6 laptop. For a while simply closing the lid put the laptop to sleep correctly. The last few months though that stopped. It would sleep but randomly wake up and when I go to pull my laptop out again the next day it was totally dead. Or I'd find it awake (though closed) and just draining my battery.

I started manually running "pm-suspend" before closing the lid. However, I find that a bit annoying.

I'm wondering if I can trigger a custom  command before the logind stuff is triggered. I've read the docs for logind and couldn't find a way to do this there. The config is set to 

```
HandleLidSwitch=suspend
```

I've done some searching and couldn't find a solution (maybe due to bad search fu.)

Can anyone point me in the right direction please?

Thank you!

---

