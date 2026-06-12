---
title: "Risks of using an older PPA ?"
date: 2013-04-30
forum: General Help
---

### Post by GameX2 on 2013-04-30
Hi,


There's a few softwares that I can't install on Raring yet, since I believe the PPAs are not updated yet for it.  One of the reasons I updated to Raring, was to use the Clementine-Lense-Music.  It's availible on Precise, but it's buggy (The lens can play an whole album, but not individual songs).  The developper released a fix for Quantal (I can't fix it under Precise.  Maybe I'm not good, or it's just not possible yet?).  I've asked the developper if he planned to release a fix for Precise, and unfortunately haven't got a reply.

The PPA is not availible under Raring yet (404: not found).  So I've tried something - I've opened the Softwares Sources (software-properties-gtk), and modified " ppa:markjtully/ppa raring " to " ppa:markjtully/ppa quantal ".  After a logoff, the lens is working perfectly! :O

I was wondering if there is a risk, maybe with security/stability, when using an older PPA like I'm doing (It seems to be the only availible option, for now) ?
Can I safely do this for my non-working software (I have other lens that aren't updated to Raring yet) ?  That'll be great.

Thanks

---

### Post by matt_symes on 2013-04-30
Hi

One of the biggest causes of dependency problems are mismatched sources; so yes, there is a risk involved.

Kind regards

---

### Post by GameX2 on 2013-04-30
> **matt_symes said:**
> Hi

One of the biggest causes of dependency problems are mismatched sources; so yes, there is a risk involved.

Kind regards

Even for an "innocent" small Unity-Lens ?

Is there another workaround?
Thanks for the fast reply.

EDIT: Reading this, now:
[http://askubuntu.com/questions/87407/risk-involved-with-using-ppa-from-old-release](http://askubuntu.com/questions/87407/risk-involved-with-using-ppa-from-old-release)

---

### Post by matt_symes on 2013-04-30
Hi

> **GameX2 said:**
> Even for an "innocent" small Unity-Lens ?

LOL :D. 

I believe some lens' are written in python. That should be all right but as I'm not using Ubuntu i cannot check.

> Is there another workaround?
Thanks for the fast reply.

EDIT: Reading this, now:
[http://askubuntu.com/questions/87407/risk-involved-with-using-ppa-from-old-release](http://askubuntu.com/questions/87407/risk-involved-with-using-ppa-from-old-release)

The main work around, as stated by the link above, is to build from source. It will link into the correct libraries - assuming it builds.

Kind regards

---

