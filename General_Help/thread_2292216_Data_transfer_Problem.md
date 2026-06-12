---
title: "Data transfer Problem"
date: 2015-08-26
forum: General Help
---

### Post by Sharidpxc on 2015-08-26
Hi, 
I am an Ubuntu 14.04 LTS user(new). My laptop configuration is core i3(4th gen.), Ram 4GB, OS 64 bit. Problem is, whenever I tried to transfer any file or any data from pc to pen drive or pen drive to pc it takes huge painful time :( ; even it occurs if I copied anything within my pc one folder to another. And that time total PC started to act like a unbelievable slowcoach, in some extent hanged also.

I badly need the solution of this. So, if there's any solution please help me out.

Thanks in advance!

---

### Post by HermanAB on 2015-08-26
Howdy,

There are some old USB bugs that affect certain hardware.  

You should try the ionice command:
$ ionice -c3 "cp filefrom fileto"

or
$ ionice -c3 bash

then everything done inside bash will be ioniced.

---

