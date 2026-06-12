---
title: "How do you disable error reporting in Lubuntu 12.10?"
date: 2013-03-01
forum: General Help
---

### Post by iamnotmyusername on 2013-03-01
Like the title says..I am trying to disable any of the dialogs that ask me if I want to report an error. I am not sure how to do this in Lubuntu. Thanks for any help.

---

### Post by oldos2er on 2013-03-02
```
sudo nano /etc/default/apport
``` Change enabled=1 to enabled=0

---

### Post by iamnotmyusername on 2013-03-04
Thanks oldos2er!

---

