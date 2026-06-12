---
title: "Can I uninstall Sylpheed from Lubuntu?"
date: 2014-01-18
forum: General Help
---

### Post by matospalka on 2014-01-18
Hi,

I have simple question - can I uninstall Sylpheed from Lubuntu?

Why am I asking - when I try it, synaptic told me, that I have to uninstall whole LXDE-desktop. 

I cant understand why?

Thanks

---

### Post by vasa1 on 2014-01-18
Yes, you can uninstall the package. See 
[https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)
[http://www.mail-archive.com/lubuntu-desktop@lists.launchpad.net/msg03490.html](http://www.mail-archive.com/lubuntu-desktop@lists.launchpad.net/msg03490.html)
and
[http://ubuntuforums.org/showpost.php?p=12389408&postcount=5](http://ubuntuforums.org/showpost.php?p=12389408&postcount=5)

---

### Post by matospalka on 2014-01-18
So if I will do that, I will remove only Sylpheed, and "meta-package" lubuntu-desktop. But this "meta-package" is only some "list" of applications, but its empty, and by uninstalling it "nothing" happens?

Sorry for my stupid questions, but I am new to Linux...

---

### Post by vasa1 on 2014-01-18
> **matospalka said:**
> So if I will do that, I will remove only Sylpheed, and "meta-package" lubuntu-desktop. But this "meta-package" is only some "list" of applications, but its empty, and by uninstalling it "nothing" happens?

Sorry for my stupid questions, but I am new to Linux...
Nothing happens. The problem that could arise is if you want to upgrade from your current version of Lubuntu to the next version instead of doing a clean new install. In that case, you'll need to reinstall lubuntu-desktop just before you upgrade so that the upgrade process has the "list" to look at.

---

