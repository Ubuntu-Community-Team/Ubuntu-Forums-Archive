---
title: "Disable hibernating with encrypted swap"
date: 2012-12-05
forum: General Help
---

### Post by zombifier25 on 2012-12-05
So, I followed [this tutorial](https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap) to set up hibernating with an encrypted swap. After completing, it turns out hibernating doesn't really work very well, so I would like to revert the changes. So how do I do that?

Any help is appreciated.

---

### Post by zombifier25 on 2012-12-09
bump

---

### Post by zombifier25 on 2012-12-09
I decided to do everything myself. I tracked down all the edited files, reverted them to the original state, then [followed these steps](http://www.logilab.org/blogentry/29155) to remove encrypted swap completely, and then started off fresh.

---

