---
title: "Netatalk 3.1.7 image transfer problem"
date: 2015-09-30
forum: General Help
---

### Post by siebe-claes on 2015-09-30
I have a Ubuntu server 14.04 LTS running a ZFS pool. I access the shares on this server using afp from my Mac running Yosemite 10.10.5. The server is running netatalk version 3.1.7.

When I open a jpeg image on my Mac that is stored on the afp share, around 30% of the time, the image gets cut off around the middle and the bottom part is just a block of a single color. When I copy the same file from the server to my laptop using scp, the image is completely fine. I don't know why this is happening but I think it started after upgrading netatalk from 3.0.8 to 3.1.7.

Any ideas on how I could solve this?

---

