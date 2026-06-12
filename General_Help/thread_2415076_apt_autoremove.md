---
title: "apt autoremove"
date: 2019-03-19
forum: General Help
---

### Post by john-fanmaker on 2019-03-19
Trying to update from 14.04 to 16.04.
Got message not enough space in '/boot, so as suggested, I used terminal/ sudo apt autoremove, only to be told autoremove was an invalid operation.
Request help, please.
John

---

### Post by CatKiller on 2019-03-19
Apt as a command was introduced with 16.04, IIRC, which you aren't on yet. Use ```
sudo apt-get autoremove
``` instead.

---

### Post by john-fanmaker on 2019-03-19
Thanks, but I had already done that, as I'd miss-read the suggestion.
However, the end result was the same - still getting the same message in terms of not enough space in '/boot.
John

---

### Post by CatKiller on 2019-03-19
Well, it's a messy task. There are a lot of posts about it. The size of the default /boot partition wasn't large enough for the not-aggressive-enough pruning. You need to remove each of the kernels you aren't using. It's doable, but a pain.

At this point in 14.04's lifetime I'd just do a fresh install of one of the newer LTSes, personally. Takes about 15-20 minutes, if your backups are up-to-date. Longer if not.

---

### Post by deadflowr on 2019-03-20
apt is available as a command dating back to at least 14.04.
But it does not include a few commands such as autoremove.
(Basic commands such as update and upgrade/full-upgrade are available on 14.04)

And autoremove in 14.04 does not have the ability to remove old kernels.
(Which is what you need to cleanup in the /boot partition)
For that you need to run some sort of manual command.
(And do not just delete files, that will cause even worse problems)

There are several to choose from but the simplest is probably purge-old-kernels.
purge-old-kernels is installed in the package called bikeshed for 14.04.
Newer releases such as 16.04 or 18.04 purge-old-kernels is part of the byobu package
To install on 14.04
```
sudo apt install bikeshed
```
to use it
```
sudo purge-old-kernels
```

---

### Post by john-fanmaker on 2019-03-20
Thanks everyone.
I've finally got around to installing 16.04, somewhat slowly, but it's done !
Regards all,
John

---

