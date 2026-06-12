---
title: "Any grouped packages?"
date: 2005-07-13
forum: General Help
---

### Post by Per M. on 2005-07-13
Is there any "grouped" packages? I mean that if I for example wanted to download an extra application package for Ubuntu, sometimes they require about 20 other files to run! Isn't there an easier solution than downloading all those files separately?

Per M.

---

### Post by Leif on 2005-07-13
What difference does it make ? Everything is taken care of automatically for you. And all the little extras that get downloaded are usually libraries, which may be used by many programs. Having them separate cuts down on disk usage.

---

### Post by Xian on 2005-07-13
If the package is in apt you can build the dependencies using that application.
```
$ sudo apt-get build-dep <package_name>
```

---

