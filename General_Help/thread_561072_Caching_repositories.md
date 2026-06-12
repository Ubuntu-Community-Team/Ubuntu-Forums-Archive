---
title: "Caching repositories"
date: 2007-09-27
forum: General Help
---

### Post by brettg on 2007-09-27
Hi all

A long standing frustration of mine is when it comes to repositories and the caching of them.

I used to use apt-proxy, but I found it to be too erratic and unstable. It also failed to cache large files (yes openoffice, I'm looking at you), so some time back I changed over to apt-cacher.

I like apt-cacher much better, but frustratingly, it still refuses to cache openoffice. I am assuming it has a cache_max_file_size setting in it, only I don't know if it is hardcoded or a configurable option. I can find nothing on google regarding this.

So, my question is, can I add a line to apt-cacher.conf to up the max file size or should I try yet another proxy app? Maybe Approx? Or will Approx do the same thing?

Any ideas?

---

