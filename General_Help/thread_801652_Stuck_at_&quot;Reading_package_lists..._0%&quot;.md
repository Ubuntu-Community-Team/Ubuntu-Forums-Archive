---
title: "Stuck at &quot;Reading package lists... 0%&quot;"
date: 2008-05-20
forum: General Help
---

### Post by gmyx on 2008-05-20
The last time it worked was over the week-end. Since then 'apt-get' (or any other process requiring the package lists) does not go anywhere else but "Reading package lists... 0%"

I did try
```
sudo dpkg --configure -a
```
With no messages - so it's not complaining.

From other posts my sources.list file is correct for 8.04. The last thing I did was patches.

Any help much appreciated.

Thank you.

Update: It seems my file system needed fixing. I went into recovery mode and did a fsck and it fixed my problem.

---

