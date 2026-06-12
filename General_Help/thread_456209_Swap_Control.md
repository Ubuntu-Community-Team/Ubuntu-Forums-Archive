---
title: "Swap Control"
date: 2007-05-27
forum: General Help
---

### Post by Mikey_MW on 2007-05-27
Hi, I installed xubuntu on my Dell Latitude C400 and I'd like to be able to get it to stop using swap space instead of ram. In normal usage it uses about 160-180 mb ram and about 30 mb swap. I haven't actually used over the 256 mb that is installed on this laptop.

The reason for trying to get rid of the swap is because of my battery life. Windows gave me 4 hours battery life (constant massive swapping, and having to run at 1.4ghz to get decent speed). Xubuntu gives me 7.5 hours (tiny swap, and its responsive at only 700mhz :) ) So now I want to try and get rid of all swap since that seems to be the main reason for the difference in battery life.

Thanks

---

### Post by reacocard on 2007-05-27
> **Mikey_MW said:**
> Hi, I installed xubuntu on my Dell Latitude C400 and I'd like to be able to get it to stop using swap space instead of ram. In normal usage it uses about 160-180 mb ram and about 30 mb swap. I haven't actually used over the 256 mb that is installed on this laptop.

The reason for trying to get rid of the swap is because of my battery life. Windows gave me 4 hours battery life (constant massive swapping, and having to run at 1.4ghz to get decent speed). Xubuntu gives me 7.5 hours (tiny swap, and its responsive at only 700mhz :) ) So now I want to try and get rid of all swap since that seems to be the main reason for the difference in battery life.

Thanks

Just comment out or remove the swap partition's line from /etc/fstab to disable it. If you want the HD space back, you'll have to adjust your partitions with a partitioner like GParted.

---

