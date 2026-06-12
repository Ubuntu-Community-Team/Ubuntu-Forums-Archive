---
title: "console login bug - can not enter password at all"
date: 2019-02-26
forum: General Help
---

### Post by marchello_lippi2 on 2019-02-26
Hi all, 

I experience weird bug in console (Ctrl+Alt+F1...)

```

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.6 LTS
Release:        16.04
Codename:       xenial

```

So, it does not allow me to login at all when using console (works well in x-windows GUI though). 
Once I press Ctrl+Alt+F1 or other F... button, it asks me to enter my login. 
After I enter my login, it should wait for entering password, right? But no way. It displays password prompt, yes. But it doesn't wait for it. Once I enter login, it displays password prompt, but immediately shows "login incorrect" error and asks for login again. 

Please advise.

---

### Post by sisco311 on 2019-02-26
It's a known bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1813873](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1813873)

---

### Post by marchello_lippi2 on 2019-02-26
> **sisco311 said:**
> It's a known bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1813873](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1813873)
Thanks, will wait till the fix is available in official repository.

---

### Post by sisco311 on 2019-02-26
You're welcome!

If you want to test the new kernel, you can install it from the proposed repository: [EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

---

