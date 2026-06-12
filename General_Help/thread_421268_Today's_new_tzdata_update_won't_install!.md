---
title: "Today's new tzdata update won't install!"
date: 2007-04-24
forum: General Help
---

### Post by Fireblend on 2007-04-24
I click on update, the installing software window appears, and then it closes, it looks for updates again and it doesn't get deleted, it's like it can't be installed. Also curiously, it says "Download size: none" is that normal?

Is it broken? Help! I wanna get that orange box out of my notification bar.

---

### Post by phidia on 2007-04-24
Well I don't even like to do every update that comes along but my update manger doesn't close the way you've  described and it shows the package size as 307kb. I'm using feisty final release. For the hey of it I just used the update manger and tzdata installed without a problem.

---

### Post by Fireblend on 2007-04-24
O.o now that's weird. I'm using feisty final as well, have rechecked updates several times.

---

### Post by Spr0k3t on 2007-04-24
Try performing the update via the terminal/console: ```
sudo aptitude update
sudo aptitude upgrade
```...and see what comes of that.

---

### Post by Scurra on 2007-04-24
Hi,

I had a similar problem using update manager today - the package is on the mirror I'm using, but doesn't seem to be signed correctly. Doing an apt-get update; apt-get upgrade gives

```
Get: 1 http://ftp.ticklers.org feisty-updates/main tzdata 2007e-0ubuntu0.7.04 [314kB]
Fetched 314kB in 0s (857kB/s)
Failed to fetch http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/pool/main/t/tzdata/tzdata_2007e-0ubuntu0.7.04_all.deb  MD5Sum mismatch
```

Is this just a problem with the mirrors?

---

### Post by Fireblend on 2007-04-24
Exact same thing as the above poster happens to me. I guess it will be solved eventually so I'll just check back later today...

---

### Post by Scurra on 2007-04-24
(works for me now using ftp.ticklers.org)

---

### Post by PartisanEntity on 2007-04-24
Same problem for me, I posted about it [here]("http://ubuntuforums.org/showthread.php?t=419874&highlight=tzdata"). Still can't update this file due to an authentication error.

---

### Post by PartisanEntity on 2007-04-24
I got it to work by opening Synaptic Package Manager > Settings > Repositories and then selecting a different server for 'Download from:'.

---

