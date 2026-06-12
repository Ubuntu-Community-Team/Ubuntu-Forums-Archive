---
title: "Couldn't find package package error in terminal ?"
date: 2007-11-21
forum: General Help
---

### Post by ToM-X on 2007-11-21
Hey,

 Having a problem on my mates laptop with ubuntu 7.10, Every time we try to install a package Example: "sudo apt-get install amsn " it comes up with the same thing everytiime

 jamie@jamie-laptop:~$ sudo apt-get install amsn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package amsn
jamie@jamie-laptop:~$ 

I personally don't have this problem and yet to find a solution on a search engine, Any help would be greaty appreciated.

 Tom

---

### Post by monktbd on 2007-11-21
the universe repository is probably not enabled on your mates laptop.
see [this link](http://www.psychocats.net/ubuntu/sources) for some explanations on how to add additional repositories to your sources.list.

---

