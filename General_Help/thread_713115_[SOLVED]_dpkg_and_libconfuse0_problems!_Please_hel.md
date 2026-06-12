---
title: "[SOLVED] dpkg and libconfuse0 problems! Please help"
date: 2008-03-02
forum: General Help
---

### Post by lambono on 2008-03-02
Hi,
When opening Synaptic I get the following error 

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

I tried running dpkg --configure -a but it fails with this error 

```
sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/available' near line 2 package `libconfuse0':
 value for `status' field not allowed in this context

```

Same thing happens when trying to run any apt commands.

Any ideas?
Im stuck!

---

### Post by lambono on 2008-03-02
The start of /var/lib/dpkg/available is...
```

Package: libconfuse0
Status: install reinstreq half-installed
Priority: optional
Section: libs
Version: 2.5-3

```

---

### Post by lambono on 2008-03-02
Sorted...

Found the answer in this thread 
[https://answers.launchpad.net/ubuntu/+question/10265](https://answers.launchpad.net/ubuntu/+question/10265)


> sudo dpkg --clear-avail && sudo apt-get update

Now working as normal :)

---

