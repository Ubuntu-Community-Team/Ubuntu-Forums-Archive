---
title: "How can you tell what packages are in a debian package repository?"
date: 2007-08-05
forum: General Help
---

### Post by qopit on 2007-08-05
I've been digging through google and the man pages for apt-get,, aptitude, sources.list, dpkg, etc to try and figure out what packages are available in a particular repository listed in /etc/apt/sources.list, but can't figure it out.

How do you figure out what deb packages are available in a specific repository?  eg: I'm very curious what the list of available packages is (besides picasa) in the google repository:

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

---

### Post by the yawner on 2007-08-06
I suppose you could disable some of the sources and reload synaptic?

---

### Post by qopit on 2007-08-06
I assume you mean to try and look and see what is missing?  Seems difficult... there must be an easier and more direct way, no?

---

### Post by nitro_n2o on 2007-08-06
```
dpkg -l 
```will give everything almost 
```
sudo aptitude
``` will give you some console interaction

---

### Post by qopit on 2007-08-06
I think I'm missing something... how can I tell exactly what is in a given repo?  "dpkg -l" lists what I've already got.

Again, an example of what I want to know is what deb packages google feels they should make available in the repo they put together (url in my first post).  Google has yet to do me wrong and I'm curious what they feel is good for linux.

It seems what I want is to get the contents of packages.gz for  a given repo, but I don't know how to achieve this (or if I'm even right in thinking that).

---

### Post by nitro_n2o on 2007-08-06
ok here are all packages for feisty security (main) [http://security.ubuntu.com/ubuntu/dists/feisty/main/debian-installer/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty/main/debian-installer/binary-i386/Packages.gz) browsing these isn't actually as easy as u want 
hope that helps

---

### Post by qopit on 2007-08-06
If I could get the Packages.gz for the google repo that way it would be perfect (grep makes the navigation easy), but I tried that way before and it didn't/doesn't work.

[http://dl.google.com/linux/deb/packages.gz](http://dl.google.com/linux/deb/packages.gz)

I actually never tried it on another repo so that is certainly an interesting way to get it for other repos.

I'm amazed there appears to be no other way... how does "apt-get update" do it, I wonder?  Hmm.

---

