---
title: "Package Manager Problem"
date: 2008-02-20
forum: General Help
---

### Post by D-Rick86 on 2008-02-20
Hey everyone!

Coming off a fresh install of Gutsy and Wine, I tried to get into my Synaptic Package Manager and I get an error that reads:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried to run that command in the terminal, but all that comes up is a ">" which doesn't do too much. 

How do I go about getting this to work? Thanks.

~Derek

---

### Post by overdrank on 2008-02-20
> **D-Rick86 said:**
> Hey everyone!

Coming off a fresh install of Gutsy and Wine, I tried to get into my Synaptic Package Manager and I get an error that reads:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried to run that command in the terminal, but all that comes up is a ">" which doesn't do too much. 

How do I go about getting this to work? Thanks.

~Derek

HI and did you run the command as root
```
sudo dpkg --configure -a
```

---

### Post by D-Rick86 on 2008-02-20
DOH! haha thanks a bundle!

Still getting used to this Linux stuff...

---

