---
title: "[SOLVED] Lightning plugin for Thunderbird only works from repos"
date: 2008-04-07
forum: General Help
---

### Post by hpalma on 2008-04-07
I'm using Hardy.
It seems that if i install the lightning thunderbird plugin from the repos it runs just fine. If i install the XPI directly from the web site the plugin doesn't work at all. I get a really weird view with a split screen and i can't see any appointments.

Any idea why this happens ?
Thanks

---

### Post by Oldsoldier2003 on 2008-04-08
> **hpalma said:**
> I'm using Hardy.
It seems that if i install the lightning thunderbird plugin from the repos it runs just fine. If i install the XPI directly from the web site the plugin doesn't work at all. I get a really weird view with a split screen and i can't see any appointments.

Any idea why this happens ?
Thanks
its probably due to the fact that Hardy is still beta and the plugin on the site just doesn't take into account some of the changes that have occurred in Hardy. If you absolutely must have the latest version of the plugin I would suggest compiling it form source. Although this isn't the "silver bullet" since again Hardy's beta status and rapid updates this close to release make it a fast moving target.

---

### Post by hpalma on 2008-04-08
As it turns out the only thing i had to do was install libstdc++5 and it worked just fine.

---

