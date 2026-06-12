---
title: "error pop-up in almost every operation."
date: 2020-04-08
forum: General Help
---

### Post by shubham623sharma on 2020-04-08
I freshly installed ubuntu 18.4.04 and I wanted to customize it so I found a video on youtube says **30 Things to do After Installing Ubuntu 18.04 LTS (all-in-one video) **and I followed things that I want, one of those things was themes. He installed a theme called**flat-remix **and here is messed up from that moment anything I’m doing on synaptic package installer or on the terminal it shows error addressing **flat-remix**. I'm attaching some screenshots that might explain.

  [https://youtu.be/BLVtxpm5c2A](https://youtu.be/BLVtxpm5c2A) link for a video that I follow.

shubham@shubham-inspiron:~$ sudo apt-get autoremove
[sudo] password for shubham: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up flat-remix-gnome (20191117) ...
/var/lib/dpkg/info/flat-remix-gnome.postinst: 4: /var/lib/dpkg/info/flat-remix-gnome.postinst: make: not found
dpkg: error processing package flat-remix-gnome (--configure):
 installed flat-remix-gnome package post-installation script subprocess returned error exit status 127
Errors were encountered while processing:
 flat-remix-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by sdsurfer on 2020-04-08
> /var/lib/dpkg/info/flat-remix-gnome.postinst: 4: /var/lib/dpkg/info/flat-remix-gnome.postinst: make: not found

I may not be reading this correctly so it may not help, but can you confirm make is installed? In a terminal,

```
make --version
```

 Ubuntu installs 4.1 so you should already have it, just to confirm.  Maybe it's looking for it somewhere else, it **should** be in /usr/bin, you can find out by

```
which make
```

---

### Post by shubham623sharma on 2020-04-09
what you asked is alright. its anything else. 
p.s. its something about **status 127. **I tried to remove it through syneptic.

---

