---
title: "My Linux Partition IS Running Out of Room"
date: 2006-07-06
forum: General Help
---

### Post by Johnsie on 2006-07-06
I'm running out of room in my ubuntu partition but have loads to spare in my Windows partition. Any chnace I can take the free Windows space and add it to my ubuntu space? How exactly would I go about doing that?

---

### Post by aysiu on 2006-07-06
If your Windows partition is before your Ubuntu partition, then, no.

You can slim down your Ubuntu partition in other ways. ```
sudo apt-get clean
``` for example, will get rid of all the installer files for your applications--the ones that live in /var/cache/apt/archives.

Can you give us a better idea of your partitioning scheme and how much room you have left?

---

