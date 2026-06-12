---
title: "Can't boot past Emergency Mode."
date: 2018-01-19
forum: General Help
---

### Post by amadis2009 on 2018-01-19
Have been trying for two days to figure out why I'm stuck in Emergency Mode with no luck. The first issue was my browser crashing and then not being able to restart it. I logged out, then couldn't log back in. Tried restart and got super long boot times (5-10 minutes). I finally got my Windows 7 partition to boot, albeit everything was running slowly. As for my Ubuntu partition, I couldn't get past Emergency mode. I tried journalctl -xb, with I/O errors. I tried switching out the PSU in case it was failing. No change. I ran memtest86+ for errors with RAM and CPU. 3 passes and no errors. I thought maybe one of my hard drives was failing, so I removed the secondary hard drive to rule it out. Now booting process happens super fast as it originally did (SSD), so maybe there is a problem with that drive. But I still can't get past emergency mode for Ubuntu. I tried journalctl -xb again with different results. This time I'm getting "unit home.mount has failed." I tried booting into a liveusb. When I open a root nautilus window and find my home folder it says "contents: nothing" and the folder is empty. I can seemingly browse all of my other folders on my Ubuntu partition, just the home folder is empty. Is it really gone? Or do I need to change something in fstab? since the second drive is no longer connected?

---

