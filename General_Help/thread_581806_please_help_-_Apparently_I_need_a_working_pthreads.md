---
title: "please help - Apparently I need a working pthreads installation"
date: 2007-10-19
forum: General Help
---

### Post by Light- on 2007-10-19
Hi,

I'm trying to run a ./configure script (for Aegisub). However, it complains with this:

> 
checking for convert... /usr/bin/convert
checking for the pthreads library -lpthreads... no
checking whether pthreads work without any flags... no
checking whether pthreads work with -Kthread... no
checking whether pthreads work with -kthread... no
checking for the pthreads library -llthread... no
checking whether pthreads work with -pthread... yes
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE
checking if more special flags are required for pthreads... no
checking whether pthreads works... no

configure: error: You need a working pthreads installation.
See `config.log' for more details.

I have tried using synaptic to search for pthreads, and install relevant packages, and also for posix and install relevant packages. However that error still keeps coming up. 

I am running Ubuntu 7.10 amd64 edition. The program i'm trying to compile was written in c++ if thats any help.

Can someone please help me?

Cheers,
Light-

---

### Post by Light- on 2007-10-19
solved: i had to install g++

---

