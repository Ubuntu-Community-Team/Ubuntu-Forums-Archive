---
title: "Ubuntu software application"
date: 2020-04-14
forum: General Help
---

### Post by tej1821 on 2020-04-14
The Ubuntu software application window has become transparent for some reason. Rebooting didn't fix. Attached screenshot.

---

### Post by Dennis N on 2020-04-14
On Ubuntu 20.04 beta, I saw this transparency with the snap version of Ubuntu Software (actual name is snap-store). It was o.k. at first, but then turned transparent (possibly after the update to the latest revision). I deleted the snap version and installed the apt version from the Ubuntu repository. 

Using terminal:

Remove the snap version of Ubuntu Software:
```
snap remove snap-store
```

Install the apt version:
```
sudo apt install ubuntu-software
```

(In my case, there was another reason to do this: to get the Flatpak support that (at least for now) only comes with the apt version of Ubuntu Software.)

---

### Post by tej1821 on 2020-04-15
Thanks! That worked. I thought it was an issue since I was on the same 20.14 beta.

---

