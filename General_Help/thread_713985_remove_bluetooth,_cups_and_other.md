---
title: "remove bluetooth, cups and other"
date: 2008-03-03
forum: General Help
---

### Post by rishav on 2008-03-03
i don't need bluetooth, cups, hp and some other stuffs, They unnecessarily starts up and wastes startup time and memory. So i decided to remove them but most of the things like bluetooth and cups removal requires removal of Ubuntu-desktop so i cant remove them. The main reason for removing them is they waste my internet bandwidth via automatic update. How can i get rid of them?

---

### Post by diskotek on 2008-03-03
i use ===> preferences/sessions (start-up) to close some of the processes. 

but preferences/seesions doesn't show every programmes. there is a breif explanation about how to shut down ueless proceses for your computer usage.

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by Arthur Archnix on 2008-03-03
Hi, you can remove them safely. Ubuntu-desktop is a meta-package. It just means that it's a fake package that actually just lists a whole bunch of other packages. Some of those that you want to remove are listed by the ubuntu-desktop package.

However, you should know that by removing ubuntu-desktop, or ubuntu-standard, or any other similar meta-package, you may expereince difficulties upgrading to a new version. For example, I've removed all the meta-packages and so I'm going to have to download a cd of Hardy and reinstall fresh. 

If you're ok with reinstalling every six months or so, or you don't plan on upgrading then don't worry about removing the package.

It's possible to prevent any upgrades of these packages by going into synaptic, and instead of choosing remove, you can lock the version. So that it's never upgraded. This is probably a bad idea though, because you won't be getting any security updates for these packages. Even if you're not using them on a regular basis, it's still a weak point in your security.

So those are your options. Remove and maybe have trouble upgrading later on. Lock them and maybe introduce some security vulnerabilities. Or continue on as you were.

---

