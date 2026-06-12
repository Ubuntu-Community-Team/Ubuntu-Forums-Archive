---
title: "Which version of xorg does Kubuntu use?"
date: 2006-11-17
forum: General Help
---

### Post by bfootdav on 2006-11-17
Hello all, an odd but hopefully simple question.  I'm currently running Debian Testing and have this brand new cool widescreen LCD monitor that isn't displaying properly in Debian.  Basically there's an extra 2 inches of space on the top of the screen.  When I ran the latest version of the Kubuntu live CD everything was displayed properly.  I carefully compared the two xorg.conf files but could find only one difference (the "i2c" module) which didn't help at all.  Unless someone knows something interesting to try I'm thinking maybe it's the version of xorg I'm running.  Debian Testing is using 7.1.0-5.  I can't figure out what version Kubuntu is using, so if anyone knows I'd appreciate the information.

Thanks,
Dave

---

### Post by taurus on 2006-11-17
From a terminal, type

```
X -version
```

---

