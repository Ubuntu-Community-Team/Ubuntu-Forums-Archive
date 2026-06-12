---
title: "HylaFAX &amp; Ubuntu"
date: 2005-05-12
forum: General Help
---

### Post by taunus on 2005-05-12
Hello all,
I installed yesterday by live CD Ubuntu on my computer. It works very fine, and I as a absolutely newcomer was able to install it, install Samba and to see the rest of my small home network.  :-P 
But I couldn’t install the HylaFAX package. 
sudo apt-get install hylafax-server 
leads to a error message that this package is not available. So now my questions:
1.	how can I install this package.
2.	does anybody has experiences with Ubuntu and HylaFAX, does it work properly together?
3.	does anybody know a better package than HylaFAX. I receive approximately 10-15 fax each day and every fax contains roughly 40-80 pages

Thanks for your support  :) 
Felix from Germany

---

### Post by lao_V on 2005-05-12
Log into synaptic and search for hylafax to see if its available and/or under any other name

---

### Post by taunus on 2005-05-12
Thx for the tip,
I just tried it out, but there is no HylaFAX in synaptic. I do not know which other name could I use to be succesfull.
I attached how I tried to install HylaFAX, maybe the command was wrong?

ubuntu@ubuntu:~$ sudo apt-get install hylafax-server
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package hylafax-server
ubuntu@ubuntu:~$

---

### Post by taunus on 2005-05-13
Is nobody able to help me with this Problem? :-? 
Or can somebody give me a tip for another good fax package tool???
thx Felix

---

### Post by lao_V on 2005-05-13
If you can't find it in the repositories then maybe its not available..have you enabled the extra repositories (universe multiverse)? If not have a look [here]("http://www.ubuntuguide.org/#extrarepositories") on how to do that

---

### Post by taunus on 2005-05-17
Hello Lao,
thx for the tip, it worked!
Regards Felix

---

### Post by lao_V on 2005-05-17
[QUOTE=taunus]Hello Lao,
thx for the tip, it worked!
Regards Felix[/QUOTE]

Have fun!!

---

