---
title: "Can't install security updates"
date: 2008-06-22
forum: General Help
---

### Post by titan124 on 2008-06-22
So I just installed Ubuntu for my first time, and now whenever I try to install security updates I get the following message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried entering dpkg --configure -a into the terminal but it said I didn't have proper access (weird, considering I'm the admin). Can anyone help me out?

EDIT: I should add that I am running 8.04

---

### Post by brian_p on 2008-06-22
> **titan124 said:**
> So I just installed Ubuntu for my first time, and now whenever I try to install security updates I get the following message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried entering dpkg --configure -a into the terminal but it said I didn't have proper access (weird, considering I'm the admin). Can anyone help me out?

EDIT: I should add that I am running 8.04

You may want

```
sudo dpkg --configure -a
```

Note the 'sudo'.

---

