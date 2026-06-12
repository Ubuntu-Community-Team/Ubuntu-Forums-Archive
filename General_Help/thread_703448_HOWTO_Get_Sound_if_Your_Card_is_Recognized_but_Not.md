---
title: "HOWTO: Get Sound if Your Card is Recognized but Nothing is Happening"
date: 2008-02-21
forum: General Help
---

### Post by XVII on 2008-02-21
I was compelled to write this guide after I had a personal experience with [my sound not working]("http://ubuntuforums.org/showthread.php?t=703376").  If your card is recognized, and you get no sound errors, then is is the guide for you.

Here is what I did to fix my sound issues:

I uninstalled these packages:
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```

Then I reinstalled them:
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```

Then, It removed some packages as a side effect that I had to reinstall them:
```

sudo apt-get install gdm ubuntu-desktop

```

Then I rebooted and ran alsamixer and made sure nothing was muted and cranked all of the volumes up to max.

I hope that this will help some people.

---

