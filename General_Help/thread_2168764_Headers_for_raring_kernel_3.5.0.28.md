---
title: "Headers for raring kernel 3.5.0.28?"
date: 2013-08-19
forum: General Help
---

### Post by ronaldv on 2013-08-19
Hi,

I am running ubuntu raring 13.04 with the kernel 3.5.0.28 (because the 3.8 don´t properly work with my nouveau drivers).

Now I need to compile something so I need to install the 3.5.0.28 headers but these are nowhere to be found.

They are not in the repos:

[FONT=Courier New]sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-3.5.0-28-generic
E: Couldn't find any package by regex 'linux-headers-3.5.0-28-generic'[/FONT]


Where can i get them?



Cheers, Ronald

---

### Post by GwL3eNC on 2013-08-19
Hello, 

a few days ago another guy had a similar question, i dont know if he got an answer. I'm not shure because 
my experiences lay some time ago. Could it be, that you need to download the sources of your kernel and 
then possibly use a configure scipt option to set the path to this headers on compiling.

---

### Post by howefield on 2013-08-19
[http://packages.ubuntu.com/quantal-updates/devel/](http://packages.ubuntu.com/quantal-updates/devel/)

---

### Post by slickymaster on 2013-08-19
[https://launchpad.net/ubuntu/+source/linux-meta/3.5.0.28.44](https://launchpad.net/ubuntu/+source/linux-meta/3.5.0.28.44)

---

### Post by ronaldv on 2013-08-19
> **howefield said:**
> [http://packages.ubuntu.com/quantal-updates/devel/](http://packages.ubuntu.com/quantal-updates/devel/)

Installing these solved my problem.

---

