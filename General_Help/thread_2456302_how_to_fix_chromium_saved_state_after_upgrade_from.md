---
title: "how to fix chromium saved state after upgrade from 18.04 to 20.04"
date: 2021-01-08
forum: General Help
---

### Post by anewbie on 2021-01-08
I had a symlink of .config to chromium data under 18.04 because zfs didn't support trim and chromium was killing my ssd.

With 20.04 chromium runs in a chroot but i'm unsure where i should put the raw data that was previously symlink so chromium under 18.04 will find it.

---

### Post by anewbie on 2021-01-08
Ok. I sort of fixed it - one other issue how do i save downloaded files to /tmp/ instead of the chroot sandbox ?

---

