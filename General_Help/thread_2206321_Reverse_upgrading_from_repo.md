---
title: "Reverse upgrading from repo?"
date: 2014-02-18
forum: General Help
---

### Post by Ertai87 on 2014-02-18
I think I recently got a bad package from a repo update that broke a package I use on a regular basis.  I'd like to downgrade the package to the version that worked.  Is there a way to get an old package back, or am I stuck waiting until the package developer fixes the package?

Thanks.

---

### Post by mikewhatever on 2014-02-18
You could run the following to make sure an older version is there:
```

apt-cache show <package name> | grep Version

```
If there is an older version you want, try installing it with <sudo apt-get --reinstall install <package name=version>.

PS: Don't think "reverse upgrading" exists, but downgrading does.

---

### Post by Ertai87 on 2014-02-18
> **mikewhatever said:**
> You could run the following to make sure an older version is there:
```

apt-cache show <package name> | grep Version

```
If there is an older version you want, try installing it with <sudo apt-get --reinstall install <package name=version>.

PS: Don't think "reverse upgrading" exists, but downgrading does.

Apparently the only version in apt is the version I have which is broken.  Dangit.

---

