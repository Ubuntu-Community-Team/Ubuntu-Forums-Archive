---
title: "What is the official recommended way of upgrading a package?"
date: 2006-12-15
forum: General Help
---

### Post by dguy on 2006-12-15
Of course, this is assuming that the Ubuntu repositories has an old version of the package in question (which seems quite common).

For example, I'd like to use the latest version of GHC ( [http://haskell.org/ghc/](http://haskell.org/ghc/) ) which is currently at 6,6 but the latest version that I can install using synaptic is 6.4. I need to use a feature that was only added in 6.6, so what is the recommended way of upgrading a package?

Thanks,
Damien

---

### Post by bodhi.zazen on 2006-12-15
> **dguy said:**
> Of course, this is assuming that the Ubuntu repositories has an old version of the package in question (which seems quite common).

For example, I'd like to use the latest version of GHC ( [http://haskell.org/ghc/](http://haskell.org/ghc/) ) which is currently at 6,6 but the latest version that I can install using synaptic is 6.4. I need to use a feature that was only added in 6.6, so what is the recommended way of upgrading a package?

Thanks,
Damien

Whatever works :)

I advise [checkinstall](http://www.howtoforge.com/howto_linux_debian_deb_checkinstall) if you install from source.

See also here: [How to install anything](http://monkeyblog.org/ubuntu/installing/)

8)

---

