---
title: "[SOLVED] Updates and disk space"
date: 2008-02-05
forum: General Help
---

### Post by paintandswim09 on 2008-02-05
So I am on my Asus EeePc, and disk space is limited. I feel compelled to download and install updates. My question is this: When I download and install, say a 26MB Kernel update from canonical, does it use an extra 26MB of disk space, or does it install OVER the ~26MB old kernel stuff? And the same goes for updates to cupsys, java, etc.

---

### Post by luisromangz on 2008-02-05
Yeah, it downloads the package, and then install it. You can clean the place where packages are downloaded with

sudo apt-get clean

---

