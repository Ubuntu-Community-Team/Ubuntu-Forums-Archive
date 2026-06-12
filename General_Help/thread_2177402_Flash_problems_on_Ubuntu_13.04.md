---
title: "Flash problems on Ubuntu 13.04"
date: 2013-09-28
forum: General Help
---

### Post by nhrdls on 2013-09-28
Observing this on at least two machines, one desktop and one laptop - both running Ubuntu 13.04 64 bit. All machines are up to date in terms of updates.

After recent updates (must be during last month) the sites working earlier are broken on both Firefox and Chromium. I have firefox 23 and chromium [COLOR=#303942][FONT=Ubuntu]28.0.1500.71 Ubuntu 13.04 (28.0.1500.71-0ubuntu1.13.04.1). 

Example site is [/FONT][/COLOR]<snip> which I have used regularly for last few months, but now I can not get the login box on either browser. Tried starting new profile in firefox, but no luck. Tried in on Windows and works fine.


Any help is greatly appreciated.

---

### Post by andreazzz on 2013-09-29
Have you already tried reinstalling Flash?
```

sudo apt-get purge flash* -y
sudo apt-get install flash* -y

```

Restart your browser and try again.

Good luck!

---

