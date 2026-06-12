---
title: "skype crash"
date: 2008-02-13
forum: General Help
---

### Post by eoika on 2008-02-13
hi everybody

I have a serious problem with skype. There was an upgrade almost three days ago and after that skype crashes soon after starting.
I have tried:
1. to complete remove it (including the hidden folder .skype in my home)
2. to install an old version (I found it on the skype website)
3. to make sudo apt.get clean and then again sudo apt-get install

But it still does not work.
The only things I have done in these days with my Ubuntu 7.10 were
1. installing apache and then completely removing it after two or three hours, and I did NOT modify any of the configuration files
2. installing fluxbuntu

I do not have any idea of what to do now.

Thanks everybody.

Laura

---

### Post by taurus on 2008-02-13
Try running it from a terminal to see what the error message is.

Applications -> Accessories -> Terminal
```
skype
```

---

### Post by s1m0n13 on 2008-02-13
I ran into a similar issue after I installed nessus.  Apparently Nessus ships with an old version of the Qt4 dynamic libraries (Qt 4.0.x or 4.1.x) and then implants its path into your ld.so.conf ahead of the regular library path (where Qt 4.2 or 4.3 is residing). This causes Skype to try and load with the 'old' Qt4, which is unsupported.

I found a solution to this problem, I edited the libraries search path config file /etc/ld.so.conf (file listed below).

include /etc/ld.so.conf.d/*.conf
/usr/lib
/opt/nessus/lib

and added /usr/lib just before /opt/nessus/lib (or whatever custom path you may have). In this way programs will look for libraries in /usr/lib before everything else.

Then I ran ldconfig and now everything works just fine.

Hope this helps.

---

### Post by medomedo on 2008-02-16
Hi,

I have similar problem, When I run Skype 2.0.0.43, it crashes after 4 sec during the license window and I get "Aborted" message on the terminal. 

I have in my apt/source.list 
[http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main

I tried also the package on skupe.com but no help.

It might be the problem. I have no Nessus and I tried with dynamic and static packages in both cases it crashes. I tried to run as root but not helping. I have up-to-date Gusty laptop without camera attached to it.

Help is appreciated.   :)
medo

EDIT: I tried the /etc/ld.so.conf tip but that did not help.

---

### Post by jarvitron on 2008-03-24
I recently installed 8.04 a6 and Skype 2.0 (was using 1.4 previously) and was having Skype crash immediately after startup (would flash User Agreement and then dump core). I removed my .Skype directory and it started right up.

---

