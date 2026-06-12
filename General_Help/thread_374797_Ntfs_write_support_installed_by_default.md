---
title: "Ntfs write support installed by default?"
date: 2007-03-02
forum: General Help
---

### Post by DaMasta on 2007-03-02
I read the 13 things you should do after installing ubuntu article, one of which is installing ntfs-3g. Ubuntu found and mounted my ntfs directories right off the bat. Is it necessary to install 3g or is it already installed or what? Thanks.

---

### Post by Maestro23 on 2007-03-02
If you want read/write access on your ntfs partiton, you will need to install ntfs-3g.  You can get from their site or from the Repositories.

> sudo aptitude update

sudo aptitude install ntfs-3g


Good luck.

---

