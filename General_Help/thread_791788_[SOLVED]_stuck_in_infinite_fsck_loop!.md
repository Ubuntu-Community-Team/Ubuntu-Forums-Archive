---
title: "[SOLVED] stuck in infinite fsck loop!"
date: 2008-05-12
forum: General Help
---

### Post by kaushd on 2008-05-12
Hi All,

I powered on my laptop today & it started running an fsck on my boot disk (/dev/sda1). It complained & exited with an exit status 4, and dropped me in maintenance mode.

I've tried running an 'fsck -y /dev/sda1' which throws up hundreds of inode issues. As fsck pass 1 completes, the cycle starts again & the same inode problems are found. Nothing is being fixed. I've let this run about 2 hours now, and keep getting the same problems.

Is this occuring because /dev/sda1 is mounted as 'read-only' in maintenance mode, so no changes are being made?

How can I stop this perpetual cycle of fsck'ing - I just want to boot my system!

---

### Post by kaushd on 2008-05-12
ok, unbelievable. After running fsck for the nth time - it actually worked. System came up ok. So i guess patience is the key!

---

### Post by bingoUV on 2008-05-12
Exit status 4 means the error could not be corrected. Have you tried fscking it from a live CD? This time make it check for bad blocks too
```

fsck -y -c /dev/sda1

```

---

### Post by kaushd on 2008-05-12
hi thanks for that suggestion. yes i'll give that a go with the '-c' switch.

does the fact that fsck works on and off indicate my hdd is on the way out? or is that a normal occurance. i've made a backup of my hard disk anyhow.

---

