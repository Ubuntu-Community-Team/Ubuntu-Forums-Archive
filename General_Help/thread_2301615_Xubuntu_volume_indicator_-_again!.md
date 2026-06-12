---
title: "Xubuntu volume indicator - again!"
date: 2015-11-03
forum: General Help
---

### Post by kkaniff on 2015-11-03
Hi there,

I've got a problem that's been answered a thousand times. I'm running a fresh install of Xubuntu 14.04 and my volume indicator has disappeared. 

I've tried a tons of things including the obvious one: Panel>New Item -- Indicator Plugin. But my Indicator Plugin has no volume icon. It does have the date, time, battery, wi-fi and bluetooth icons.

Can anyone help me?

---

### Post by pqwoerituytrueiwoq on 2015-11-03
do you have indicator-sound and indicator-sound-gtk2 installed
```
apt-cache policy indicator-sound-gtk2 indicator-sound
indicator-sound-gtk2:
  Installed: 12.10.0.1-0ubuntu3
  Candidate: 12.10.0.1-0ubuntu3
  Version table:
 *** 12.10.0.1-0ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status
indicator-sound:
  Installed: 12.10.2+14.04.20140401-0ubuntu1
  Candidate: 12.10.2+14.04.20140401-0ubuntu1
  Version table:
 *** 12.10.2+14.04.20140401-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by kkaniff on 2015-11-04
> **pqwoerituytrueiwoq said:**
> do you have indicator-sound and indicator-sound-gtk2 installed ?
Man, you're the best! That was it--both items missing. Install did the trick.
Thanks again.

---

