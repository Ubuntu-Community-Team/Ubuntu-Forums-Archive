---
title: "Package install and upgrade error"
date: 2007-01-22
forum: General Help
---

### Post by gerbalblaste on 2007-01-22
When i attempt to install or upgrade a package onto my system i receive the following error:

```
dpkg: parse error, in file '/var/lib/dpkg/available' near line 13978 package 'libbluetooth2':
 'Depends' field, syntax error after reference to package 'libc6'
E: Sub process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:
```

I have no explanation for this problem. I first noticed it yesterday. It may have been occuring for some time.

---

### Post by gerbalblaste on 2007-01-22
nevermind, i solved it,
a 'Depends:' and a 'conflicts:' line had become merged in /var/lib/dpkg/available :o 

thanks anyway

---

