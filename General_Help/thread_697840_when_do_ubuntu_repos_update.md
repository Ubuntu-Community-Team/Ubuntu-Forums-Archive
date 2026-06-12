---
title: "when do ubuntu repos update?"
date: 2008-02-15
forum: General Help
---

### Post by arkara on 2008-02-15
i use ubuntu 7.10 now and i want to switch to ubuntu 8.04 because it will be a verry stable system.now i want to know how often will the repos be updated?? because i am planing to keep the lts for the whole 3 year thing... but i also dont want to loose critical new features.

---

### Post by fjgaude on 2008-02-15
AFAIK, all through the night and day. You can get to what is there by using Synaptic, and clicking Reload and then Mark All Upgrades, if there is any they will show.

---

### Post by strabes on 2008-02-15
What do you mean by "how often the repos will be updated?" Do you want to know how often new versions of packages will be added to the hardy repos? While it's under development, new packages are available practically every day. However, after the final release, updates are rarely added. See [this page](https://wiki.ubuntu.com/StableReleaseUpdates) for more information. Also, please try searching google before posting on these forums. The above page is the first result on [this](http://www.google.com/search?q=ubuntu+update+packages+after+release+policy) google search. 

If you want to upgrade your system to gutsy right now, simply open a terminal (Applications > Accessories >Terminal) and run the following command:```
sudo update-manager -d
```The "-d" flag tells update-manager to check for development releases. I, however, strongly recommend you wait until the final release. Yesterday was the feature freeze, which means no new features will be added and the rest of the development cycle will be focused on fixing bugs. This also means that hardy's current state is probably quite buggy.

By the way, ubuntu's LTS development cycle is two years, not three.

---

### Post by AndyCooll on 2008-02-15
> **arkara said:**
> i use ubuntu 7.10 now and i want to switch to ubuntu 8.04 because it will be a verry stable system.now i want to know how often will the repos be updated?? because i am planing to keep the lts for the whole 3 year thing... but i also dont want to loose critical new features.

Essentially with each release the repos are frozen. The only updates that a release version then gets are security related ones. This is for a number of reasons, for example it ensures no new packages are introduced that may affect the stability of that release. It also means developers can concentrate making sure their updates are ready for the next release.

As a rule of thumb, if you want long-term stability you are going to have to sacrifice keeping upto date with new features. Occasionally a few updates for the most popular apps appear in backports, and you can always manually install them yourself of course,

:cool:

---

### Post by arkara on 2008-02-15
so the only thing that i get with a stable release is security updates??

not any stability updates?? or patches?

---

### Post by isecore on 2008-02-15
> **arkara said:**
> i use ubuntu 7.10 now and i want to switch to ubuntu 8.04 because it will be a verry stable system.now i want to know how often will the repos be updated?? because i am planing to keep the lts for the whole 3 year thing... but i also dont want to loose critical new features.

The operative words here is "will be". Hardy is still in development and as such is not recommended on production systems. You can try it out if you want to, but don't start crying here if things don't work.

---

### Post by AndyCooll on 2008-02-16
> **arkara said:**
> so the only thing that i get with a stable release is security updates??

not any stability updates?? or patches?

Yes, there may be stabilty updates and patches too ...depending on how important they are. What you are unlikely to get are newer versions of apps that are released as upgrades. For instance you are unlikely to get newer versions of the kernel, or if Hardy is released with Firefox 2 you won't get Firefox 3 etc etc.

:cool:

---

### Post by arkara on 2008-02-22
what about the backports???
how can i install software from the backports??
will openoffice be available as from september

---

### Post by kpkeerthi on 2008-02-22
> **arkara said:**
> what about the backports???
how can i install software from the backports??
will openoffice be available as from september

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by fragos on 2008-02-22
Software sources has an "Updates" tab which allows to to request that backports be offered with other updates.

---

