---
title: "Where does a downloaded package go?"
date: 2006-07-12
forum: General Help
---

### Post by sung_bae on 2006-07-12
Hi, I was really impressed with Dapper and it has become the only one OS in my desktop. The only bad side is that I had to download many packages, emacs, latex, gcc etc., but through synaptic, it turned out to be just great.

Now I want to have the same environment in my laptop as well, but base installation from CD will need me to download all those packages again. What I'd like to do is to copy those downloaded packages from my desktop hdd and install manually on the laptop. I've been trying to locate those downloaded .deb packages but couldn't figure out which directory they are sitting in. Any help? Thanks,

---

### Post by o_fortuna on 2006-07-12
APT (which is what Synaptic uses) keeps a cache of downloaded files. Most of them -- but perhaps not all of them -- will be found in this location:

```
/var/cache/apt/archives
```

Once you have those packages, you could put them onto a cd and download them to the new machines that way.

---

### Post by sung_bae on 2006-07-12
Thanks!

---

