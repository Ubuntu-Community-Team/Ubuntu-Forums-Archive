---
title: "apt-get install thttpd -- E: Package 'thttpd' has no installation candidate"
date: 2016-12-26
forum: General Help
---

### Post by marchello_lippi2 on 2016-12-26
Hi all, 

Tried to install thttpd web server using 

```

sudo apt-get update 
sudo apt-get install thttpd

```

Got error 

> 
$ sudo apt-get install thttpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package thttpd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'thttpd' has no installation candidate


Please advise. 
Thanks ahead.

---

### Post by ian-weisser on 2016-12-26
Debian identified the 'thttpd' package as dead or orphaned in 2012. It was withdrawn from newer versions of Debian and Ubuntu at that time.
The package was withdrawn from the already-released Precise repo in Nov 2016.
It's still available in Debian Oldstable...but I recommend against using it. It was withdrawn four years ago for a good reason,

Source: [https://tracker.debian.org/news/222930](https://tracker.debian.org/news/222930)

---

