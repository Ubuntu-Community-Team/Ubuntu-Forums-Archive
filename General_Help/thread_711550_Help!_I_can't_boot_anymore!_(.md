---
title: "Help! I can't boot anymore! :("
date: 2008-02-29
forum: General Help
---

### Post by aztektum on 2008-02-29
I have a 300GB storage HD in my box that I repartitioned using the graphical tool in Ubuntu 7.10 from two chunks to one large space.

On boot I got an fstab error that it couldn't recognize the UUID for the old partitions and dropped me to an emergency shell. I removed the lines referencing the old partitions but it still won't boot! :(

I get something like Running Local Boot Scripts (/etc/rc.local) and it hangs there. It gets beyond checking my fs's.

I really don't want to reinstall! Although I could, it's just frustrating.

---

### Post by taurus on 2008-02-29
Can you post the outputs of these commands?

```
sudo fdisk -l
cat /etc/fstab
ls -la /dev/disk/by-uuid
```

---

### Post by aztektum on 2008-03-01
sorry about the delayed reply. i attached them in .txt files this is output runnin' the 7.10 livecd so i could back up data if i end up doing a reinstall

---

### Post by aztektum on 2008-03-03
oh btw i figured it out. connected the dots from the output you requested. had to replace the UUID. woot

thx

---

