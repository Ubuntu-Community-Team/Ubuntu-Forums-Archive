---
title: "firefox and ubuntu software don't launch in fresh installation"
date: 2022-12-22
forum: General Help
---

### Post by alo12 on 2022-12-22
hi,
in a fresh isntallation of ubuntu 22.04 lts neither firexox nor ubuntu software are starting. any idea about what could be wrong?

---

### Post by TheFu on 2022-12-22
> **alo12 said:**
> hi,
in a fresh isntallation of ubuntu 22.04 lts neither firexox nor ubuntu software are starting. any idea about what could be wrong?

Depends.  Is any part of your install non-standard?  What have you done before the issue happened?  I'm not sure what "firexox" is and have never used "ubuntu software", but if those are typos, then I do think that both are snap packages, so that would be my first guess lacking **any** other information.

---

### Post by grahammechanical on 2022-12-22
You say this is a fresh installation but have you removed a package called snapd? In Ubuntu 22.04 and later both Firefox and Ubuntu Software are snap packaged applications and cannot run without snapd installed. 

Regards

---

