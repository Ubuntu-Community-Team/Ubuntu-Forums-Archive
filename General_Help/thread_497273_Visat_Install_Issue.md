---
title: "Visat Install Issue"
date: 2007-07-10
forum: General Help
---

### Post by Uncle Spellbinder on 2007-07-10
No-go for me in Vista Home Premium.  After reboot, it asks for an install CD.

> LOAD INSTALLER COMPONENTS FROM CD

An installation step failed.

You can try to run the failing item again from the menu, or skip it and choose something else.  The failing step is: LOAD INSTALLER FROM CD.

Obviously, there is no CD. And none of the other items seem to apply. Trying to Install on NFTS "M" partition.

---

### Post by ago on 2007-07-10
Do a fresh install, when it stops press alt+f2 then run

```

cp   /var/log/syslog   /media/host

```

This will copy the log to your windows partition, then zip it and attach it here to your post

Thx

---

### Post by Uncle Spellbinder on 2007-07-10
Well, on the third attempt, all went well...sort of.  I uninstalled Wubi, deleted everything referencing Wubi and started fresh.  Started over and everything installed.  Booted into Ubuntu, typed password....the password is not recognized.  :(

**EDIT**

Working fine.  My error.  All installed perfectly and I'm posting here from Firefox/Ubuntu!!  :)

---

### Post by Uncle Spellbinder on 2007-07-10
Only issue is my screen resolution.  I have a 19" widescreen which needs to be set at 1440 x 900.  The highest available when I click "screen resolution" is 1280 by 1024. Everything is a bit scrunched.

I guess I'll post a topic elsewhere in the forums.  Otherwise, all is working well. Updated fine, rebooted and am able to go to either Ubuntu or Vista without error.  EXCELLENT.

---

