---
title: "Can't lock package in synaptic"
date: 2006-12-11
forum: General Help
---

### Post by temcat on 2006-12-11
Hi folks,

on Edgy I don't seem to be able to lock a package from updating in Synaptic. When I select a package and choose "Package->Lock Version", Synaptic refreshes the view, but when I look at the package, it's not locked. 

Can you confirm it on your system? Is it possible to lock package via command line? I haven't found anything like that in apt-get or dpkg manual pages.

---

### Post by mcduck on 2006-12-11
I just noticed the same thing today..

---

### Post by reztho on 2006-12-14
I can confirm this in edgy too. In dapper synaptics works fine.

EDIT: It's already reported: [https://launchpad.net/distros/ubuntu/+source/synaptic/+bug/67146/](https://launchpad.net/distros/ubuntu/+source/synaptic/+bug/67146/)

---

### Post by kaamos on 2006-12-14
There's a short guide to pinning packages at the bottom of this page ->
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)

---

### Post by mcduck on 2006-12-14
Thanks, that worked fine.

I think I'll have to check if there's already any bug report about Synaptic not being able to do this..

---

### Post by Divan Santana on 2007-01-11
that link Doesn't work darn :(

---

### Post by Divan Santana on 2007-01-11
ok oops its working now

---

### Post by UofLSpeed on 2007-01-22
Same problem here.  Thanks for the link.

---

