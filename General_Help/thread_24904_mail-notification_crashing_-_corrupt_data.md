---
title: "mail-notification crashing - corrupt data?"
date: 2005-04-08
forum: General Help
---

### Post by brickbat on 2005-04-08
hi, mail-notification is crashing.  something went crazy when i was entering an account and i think the data is corrupt but i dont know where to find it to delete it.

i ran mail-notification --help and tried all the options but there isnt one to reset the data.

my xsession.errors file says

mail-notification: ath.c:181: _gcry_ath_mutex_lock: Assertion `*lock == ((ath_mutex_t) 0)' failed

suggestions welcome

ciao,
bb

---

### Post by arctic on 2005-04-08
if you have set up a gmail account, then mail-notification won't work correctly. the developer is trying to fix the gmail bug.
if it's not a gmail account, it would be useful to know which kind of account you were using instead.
in order to get back to a clean state, uninstall the software again, clean your ~/.gconf folder. there is a folder for mail-notification. delete it. then reinstall.

---

### Post by brickbat on 2005-04-08
arctic, you are a champion.  yes, it was gmail accounts..

I even went to the effort of installing a deb package of the latest version to ensure it was not a software problem.

thanks
bb

---

