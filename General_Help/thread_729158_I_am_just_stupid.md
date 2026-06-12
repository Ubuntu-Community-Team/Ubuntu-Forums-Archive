---
title: "I am just stupid?"
date: 2008-03-19
forum: General Help
---

### Post by J$oney on 2008-03-19
jonathan@jonathan-laptop:~$ sudo apt-get install knmap 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package knmap
jonathan@jonathan-laptop:~$ 

no matter what i do this is all i get, If i try to su into root, my password that i assigned will not work and it's not letting me in. Still applying super user should allow this to work. No matter what file, package i try to install i can not do it, always the same error. What is wrong, i am new to ubuntu, i've used fedora and never had these problems.
Oh it also every once in a while will throw a missing key error as well. I have tried to apt-key add -EX:1234567 this will not work either.

---

### Post by freebios on 2008-03-19
do you have all the repository's enabled in software sources?

---

### Post by lapubell on 2008-03-19
you might need to enable some repositories.  it doesn't look like knmap is in the default repos.  Open synaptic go Settings -> Repositories and make sure that all the checks are in place for the multiverse and other repos.  then click Close, and Reload.  then search for the package and find it, install it.

Just so you know, Synaptic is jsut a frount end to apt.

---

### Post by Lord Illidan on 2008-03-19
Ubuntu and Fedora have a different way of accessing super user rights. You should read this : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

As for knmap, I have no idea if it is in the repositories, (I am not using Ubuntu atm).

Perhaps you could try searching them with synaptic, or else
```
sudo apt-cache search nmap
```

---

### Post by J$oney on 2008-03-20
Thanks that was the problem now i'll i have have it a flash issue i posted it found nothine searching for it.

---

