---
title: "3D graphics glitch"
date: 2021-04-18
forum: General Help
---

### Post by srturner on 2021-04-18
I have been running Ubuntu 20.04 for a few months with no graphics issues. Within the last week though, 3D graphics have developed a glitch. I noticed it first in Blender, in the viewport, but on testing, it is happening in other programs with 3D graphics too. It seems that some areas of small faces are disappearing, see the attached image. I wonder if there was an automatic driver update or similar that may have caused issues? I would be grateful for any suggestions! (I tried updated MESA to a newer version, with no difference).

It's just a basic laptop with onboard graphics: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display

[ATTACH=CONFIG]288337[/ATTACH]

---

### Post by CelticWarrior on 2021-04-18
Welcome.

An "[COLOR=#000000]Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics" is definitely NOT something you would want to use for Blender or any other 3D rendering or anything other than basic tasks like web browsing and media, not even games.[/COLOR]

---

### Post by srturner on 2021-04-18
Thanks. I appreciate that this is a budget setup from a few years back... so I’m not intending on playing any games or anything too intensive, but Blender has been working fine without graphical glitches up until now with some very basic modelling which is all I need it for.

---

### Post by Impavidus on 2021-04-18
Weak graphics or not, this kind of artefact shouldn't happen, in particular if it worked until last week.

I got two kernel upgrades last week on 20.10 and assume there were some on 20.04 too. Those may cause such issues. Does it work better if you boot an older kernel? If it has already been autoremoved, it can be reinstalled.
```
$ grep " upgrade linux-ima" /var/log/dpkg.log.1 /var/log/dpkg.log
/var/log/dpkg.log.1:2021-03-15 13:37:09 upgrade linux-image-generic:amd64 5.8.0.44.49 5.8.0.45.50
/var/log/dpkg.log.1:2021-03-25 10:44:11 upgrade linux-image-generic:amd64 5.8.0.45.50 5.8.0.48.53
/var/log/dpkg.log:2021-04-14 19:44:16 upgrade linux-image-generic:amd64 5.8.0.48.53 5.8.0.49.54
/var/log/dpkg.log:2021-04-16 20:01:42 upgrade linux-image-generic:amd64 5.8.0.49.54 5.8.0.50.55
```

---

### Post by srturner on 2021-04-18
Perfect! Thank you! I reinstalled an older kernel (the two last week were both causing issues, so went back a little further to last month) and now working perfectly again, thank you. Is it not recommended to continue running the old kernel? I can boot to it only when needed, if that’s better. Is it likely to auto uninstall? Hopefully a newer kernel will fix it, at some point.

---

### Post by Impavidus on 2021-04-18
Pay attention to the packages that get installed and removed. It's not recommended to run old kernels. This may get fixed in a later kernel. It may help if you report a bug: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

