---
title: "[SOLVED] Firefox Problem"
date: 2008-06-01
forum: General Help
---

### Post by john.hall on 2008-06-01
I ran apt-get remove firefox then apt-get install firefox.  Bad idea.  Now firefox crashes as any user except root.

Any ideas?

---

### Post by y-lee on 2008-06-01
Hmmm probably is a permissions issue. Check the permissions in your mozilla folder to be sure you own them and have read write access.  Note this is a hidden folder in your home directory.

In reality it might be easier to try to move rename or delete this folder and let firefox recreate it when your run it. Or to use synaptic to purge and then reinstall FF.

---

### Post by john.hall on 2008-06-01
Cool.  Thanks.

---

