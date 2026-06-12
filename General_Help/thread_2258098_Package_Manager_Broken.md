---
title: "Package Manager Broken"
date: 2014-12-24
forum: General Help
---

### Post by j0eb0b on 2014-12-24
I am trying to install updates on a 12.04 system and get the error "Broken Count >0 and additional details:

The following packages have unmet dependencies:

linux-generic: Depends: linux-image-generic (= 3.2.0.68.81) but 3.2.0.74.88 is installed
               Depends: linux-headers-generic (= 3.2.0.68.81) but 3.2.0.74.88 is installed

Is there a sticky that addresses this?

Thanks,
Joe

---

### Post by schragge on 2014-12-24
Just wait till newer version of *linux-generic* reaches your repository mirror. Maybe tomorrow or in a couple of days. Alternatively, you can temporarily remove the old version if it blocks important updates.
```

sudo apt-get remove linux-generic

```
But don't forget to install it again afterwards. While not critical, it's a very useful meta-package that always depends on the latest kernel.

---

### Post by j0eb0b on 2014-12-24
Thank you, that fixed the immediate problem.  I will try and reinstall Linux-Generic in a couple of days.

---

