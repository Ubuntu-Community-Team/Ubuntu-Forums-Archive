---
title: "apt-get versus aptitude?"
date: 2008-05-28
forum: General Help
---

### Post by Jordanwb on 2008-05-28
I guess this applies mainly to my server which is running Server edition (duh). So what's the difference from typing

sudo apt-get install foo

as opposed to

sudo aptitude install foo

:confused:

I notice apt-get has super cow powers but aptitude does not.

---

### Post by werries on 2008-05-28
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

this explains it better than i could

---

### Post by werries on 2008-05-28
essentially it just matters for package dependencies. aptitude remove automatically gets rid of unused dependencies,
apt-get can use "sudo apt-get autoremove"
its a minor difference.

---

### Post by Jordanwb on 2008-05-28
Okay do the only major difference is when the command removes unneeded packages.

Speaking of dependances I wanted to remove Lynx Browser but Synpatec said that MonoDevelop depends on it, I checked MonoDevelop's dependancies and Lynx wasn't listed. :confused:

---

### Post by lisati on 2008-05-28
> **werries said:**
> essentially it just matters for package dependencies. aptitude remove automatically gets rid of unused dependencies,
apt-get can use "sudo apt-get autoremove"
its a minor difference.

I've noticed that aptitude is better with dependencies when installing too: when setting up my copy of 7.04 (Feisty) for the first time (about a year ago), I just blindly used apt-get when following a tutorial for dealing with one problem I had. Later, when doing a fresh install as a brute-force method of fixing a couple of mistakes I'd made, I found that using aptitude reduced the number of steps I needed to install the pacakges recommended by the tutorial I'd previously followed.

In otherwords, aptitude can, in some circumstances, simplify the installation and removal process.

---

### Post by drs305 on 2008-05-28
A tag on question. 

A couple of days ago I wrote a fairly long entry concerning questions about apt-get vs aptitude. While writing the post I learned enough doing research that I decided not to post it.

One question I didn't resolve was what happens to recommended packages. That seemed to be one of the few remaining differences between the two (aptitude installs recommended packages automatically while apt-get apparently doesn't). 

I have used aptitude for anything I installed via command line. If I use apt-get to remove them, will apt-get recognize the recommended packages that aptitude installed?

Thanks.

---

