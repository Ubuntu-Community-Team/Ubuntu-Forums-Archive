---
title: "Debian - Ubuntu Migration"
date: 2007-12-07
forum: General Help
---

### Post by Awayne on 2007-12-07
I'm looking at moving a Debian Etch install over to Ubuntu. I have a seperate /home partition and was wondering if it would be possible to install Ubuntu while leaving /home intact with all the files. But when it comes to desktop configuration files and the like, I'm unsure about what would be needed. Any help would be appreciated. Thanks.

---

### Post by p_quarles on 2007-12-07
Yes, that will work. Ubuntu and Debian apps are not packaged identically, but most of them are very close to one another. The worst you'll experience are some "application not found" errors on your first bootup, because you probably have some startup settings in your home folder that refer to apps you haven't reinstalled yet. 

The other possible problem is that if Ubuntu ships with a radically different version of a package than the one in Debian stable (GIMP, for instance, or Thunderbird), you will find that you need to make changes to your menus and plugins. 

Basically, there could be a few hiccups, but nothing that a little patience won't solve. Just be sure to choose the "manual partition" option during installation, so you can designate the proper root and home partitions. The "guided" options won't let you do that.

---

