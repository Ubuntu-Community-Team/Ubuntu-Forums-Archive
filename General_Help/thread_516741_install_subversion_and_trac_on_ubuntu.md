---
title: "install subversion and trac on ubuntu"
date: 2007-08-03
forum: General Help
---

### Post by yinglcs2 on 2007-08-03
Hi, how can I install subversion 1.4.2 and trac 0.10.3.1 on my ubuntu?

i don't want the latest version because my other environment is using those 2 specified versions.

Thank you.

---

### Post by DrSpirograph on 2007-08-04
I haven't followed subversion very closely for a while, but when I did it seemed that new versions were usually backward compatible and a difference of one minor version shouldn't make a difference, so you should be fine to go ahead and use 1.4.3
But if you're certain you want to use 1.4.2, you could try getting it from the debian repository, I haven't tried these instructions myself, so use them at your own risk:

Add the main debian repository to your /etc/apt/sources.list
```
deb http://http.us.debian.org/debian stable main contrib
```
Update
```
sudo apt-get update
```
Install 1.4.2
```
sudo apt-get install subversion=1.4.2dfsg1-2
```

I don't know how you'll go with dependencies.

Then make sure you remove the debian repository from your sources.list and do apt-get update again to ensure you don't end up clobbering other files on your system with debian updates.

---

