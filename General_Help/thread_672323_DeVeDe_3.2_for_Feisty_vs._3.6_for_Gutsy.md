---
title: "DeVeDe 3.2 for Feisty vs. 3.6 for Gutsy"
date: 2008-01-19
forum: General Help
---

### Post by stchman on 2008-01-19
Hello all,

I have been wanting to make some .avi and .mpg files into a DVD.  I have read that DeVeDe will do the trick.

I also know that DeVeDe is not in the repos.  I went to [www.getdeb.net](www.getdeb.net) to get the software.

I was looking around and it appears that getdeb has V3.2 for Feisty and V3.6 for Gutsy.  I am running Feisty.

My question is what if I download the .deb for Gutsy and install it on Feisty.  Will it work?

Thanks.

---

### Post by PeterJS on 2008-01-19
The most correct answer: it might.

You could always download both and try the gutsy version first. If it has any dependencies that don't have high enough versions in the feisty repos that would explain why the feisty one is only up to version 3.2 whereas the gutsy version is up to 3.6

---

### Post by stchman on 2008-01-19
All appears to work.  The install went through and the program ran.

I tested it on a small file and it worked!!!!!!!!

---

### Post by chrisccoulson on 2008-01-19
In general, installing binary packages from other Ubuntu versions (or other distributions) is not a good idea. The reason is, these packages may have been compiled against different versions of libraries compared to the versions you have on your machine. This can lead to unpredictable behaviour or worse.

Source compatibility does not guarantee binary compatibility.

You should stick to binary packages compiled for your system. If a package doesn't exist in the repository already, there may be one on [www.getdeb.net](www.getdeb.net) or in someones PPA on Launchpad. If you require a package in a newer Ubuntu version, you could [request a backport]("https://help.ubuntu.com/community/UbuntuBackports"). Or, you could try to backport the package yourself using [Prevu]("https://wiki.ubuntu.com/Prevu"). Failing that, you could compile from source.

---

