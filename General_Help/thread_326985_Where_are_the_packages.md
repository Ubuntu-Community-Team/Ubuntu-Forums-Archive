---
title: "Where are the packages?"
date: 2006-12-28
forum: General Help
---

### Post by larini on 2006-12-28
Hi all, when I execute an apt-get install xxxx, the package is copied to any where, so I can save all these packages to reinstall in another machine again?
Thanks.

---

### Post by KenSentMe on 2006-12-28
All packages are saved in /var/cache/apt/archives. You can copy all the packages to the same folder on a new installation. This way they don't have to be downloaded again. But you need to install them all with the same apt-get install command.

---

