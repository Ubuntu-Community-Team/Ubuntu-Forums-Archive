---
title: "apt-build ignore errors"
date: 2014-01-11
forum: General Help
---

### Post by Tristan_Williams on 2014-01-11
I am trying to run the following command:
```

apt-build world --noupdate --build-only --yes --force-yes

```

However, the past few times I've done it, I get an error that says the package cannot be found (This is because it is a "binary only" package.

Every time I get this error, I go to my apt-build.list file and remove the corresponding item from the list.
So far I am have gotten to package 68 out of 315 ( I removed all of the packages that are required to compile packages, plus the kernel, from the list)
So far I have removed 21 packages from the list due to their source code not being found. 

How can I simply bypass these errors and continue with apt-build, instead of stopping apt-build and removing each package one by one until it finally goes through?

---

