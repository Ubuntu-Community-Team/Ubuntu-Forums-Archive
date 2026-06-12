---
title: "Cronjob seems not to work"
date: 2005-03-23
forum: General Help
---

### Post by Shambler on 2005-03-23
I have following crontab entry:
```
* */2 * * * wget -q -N http://xplanet.dyndns.org/clouds/clouds_2048.jpg -O /home/shambler/Wallpapers/clouds_2048.jpg
```

The strange thing is, that the file /home/shambler/Wallpapers/clouds_2048.jpg is not downloaded as it seems, since the time stamp is more than 12 hours old.

Invoking wget directly does alter the time stamp of the file, though.

---

### Post by Shambler on 2005-03-23
No ideas so far? I mean, the syntax is correct, isn't it?

---

