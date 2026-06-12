---
title: "Problems with Software Centre ..."
date: 2013-01-10
forum: General Help
---

### Post by earache0 on 2013-01-10
Hi I've been having problems, not Skype but installing stuff in general. I tried the 
sudo apt-get remove --purge software-center  sudo rm -r /usr/share/software-center/ rm -r ~/.cache/software-center/ sudo apt-get install software-center ubuntu-desktopand it failed on install:

Reading package lists... Done
Building dependancy tree
Reading state information... Done
Package software-center is not available, but it is referred to by another package
This may mean that the package is missing, has been obsoleted, or is only available from another source

E: Package 'software-center' has no installation candidate
E: unable to locate package ubuntu-desktop

so I tried
cat -n /etc/apt/sources.listand it only went as far as line 53??!!!
any help greatly appreciated

---

### Post by Bucky Ball on 2013-01-11
Hi,

Your post has been moved to a new thread of its own. Keep an eye on the other one and add anything you learn, even reference it here, but you dilute your chances of getting help by hijacking other threads. It creates confusion, dilutes community effort and reduces your chances of getting specific help with your problem.

Good luck with it and you can change the thread title to something more specific by clicking 'Go Advanced' when editing the first post.

BB

---

### Post by ibjsb4 on 2013-01-11
Do a ..

```
sudo apt-get update
```And try installing the software center again.

Ubuntu-desktop is a mega-pack, do you really need to install the entire desktop?

And your software sources can go to only line #53, just depends on what extras you have.

---

### Post by Bucky Ball on 2013-01-11
> **ibjsb4 said:**
> Do a ..

```
sudo apt-get update
```

Exactly. And perhaps immediately after that do:

```
sudo apt-get upgrade
```

This won't upgrade the release but will upgrade anything you have installed that needs to be upgraded ...

---

