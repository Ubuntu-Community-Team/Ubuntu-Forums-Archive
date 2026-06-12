---
title: "Random fsck failures during Kubuntu boot"
date: 2007-07-29
forum: General Help
---

### Post by gila_monster on 2007-07-29
Hello, all and sundry.

My laptop (running Kubuntu)  occasionally gets a fsck failure at boot time. I've had about three in two months. It's not tied to the full fsck done every 30 days on my partitions. Each time, I have restarted the laptop, and things proceed normally.

Question: is it possible for fsck to return a false positive? Or should I be looking for an intermittent failure of my drive? The lappy is only three years old, but it does see several hours of daily use. I have lost no data up to now (and I do regular backups anyway).

I did check some of the other threads on fsck failures, but I'm still running through them.

Thanks, folks!

---

### Post by rillip on 2007-07-29
I would let fsk run; it is possible to get an fsck without there really being an issue, it just has to detect that the file system didn't unmount cleanly last time.  That's proably why a reboot fixes it.  I would just let it run once to clear the error.

---

