---
title: "Root on software RAID, EVMS conflict"
date: 2006-08-20
forum: General Help
---

### Post by pestie on 2006-08-20
Hi there. I decided it was time to migrate my desktop system to a mirrored RAID1 setup, since I had two nearly-identical hard drives in there. I did that using Knoppix, and surprisingly, it went relatively easily. But now I have an Ubuntu-specific problem.

I'm running Dapper with a custom 2.6.17 kernel (no initrd). My RAID device is /dev/md0 and consists of /dev/hda1 and /dev/hdb1. My problem is that EVMS is grabbing /dev/hdb1, so when the system boots, the raid comes up in degraded mode, because /dev/hdb1 does not exist. It's been moved to /dev/evms/hdb1. If I add it back in to the RAID set with mdadm, all is fine - it syncs up and life is good. But I really just want to convince EVMS to leave everything the hell alone and just let me have my devices to myself. I know that EVMS is very cool, but I really don't need it for a home desktop PC.

Any suggestions? I did some Google searching, but I was unable to find anyone who had this specific problem. I did find people who had /dev/md0 being grabbed by EVMS, but the solutions there didn't seem to apply to my situation.

---

