---
title: "apt-get doesn't do anything...ever"
date: 2008-05-19
forum: General Help
---

### Post by alphis on 2008-05-19
Hello all. I'm a fan of comment line interfaces and I use emerge on my gentoo machines for all my portage needs. However when I try to update anything on my gutsy gibbon install via apt-get I constantly get no updates. I of course first apt-get update before trying to apt-get upgrade. However there are never any updates! It has never updated once since I've installed it!

I know there was an openSSH advisory based on debian's problem with seeding the random number generator and this directly affects ubuntu as well. I've assumed there was an ubuntu upgrade for this (and I know I read about it somewhere) but alas, when I apt-get update and then apt-get upgrade nothing happens. I know I'm using openSSH since I did this via an ssh connection to begin with. 

What exactly am I missing here?

---

### Post by Titan8990 on 2008-05-19
If you are specifically looking to upgrade ssh you can do $apt-get install ssh and it will check for new versions of ssh or any other app for that matter.

---

### Post by nobody13 on 2008-05-19
did you check /etc/apt/sources.list ?  If it's empty you'll get 

```
root@dave-desktop:/etc/apt# apt-get update
Reading package lists... Done
```

---

### Post by .nedberg on 2008-05-19
> **nobody13 said:**
> did you check /etc/apt/sources.list ?

+1

Check your sources.list! I seem to remember that is you installed gutsy without network it will comment out all your repositories in /etc/apt/sources.list. Just uncomment them or use Synaptic to reenable them.

---

### Post by alphis on 2008-05-19
/etc/apt/sources.list is just fine thanks. It doesn't update is all. Also, apt-get install ssh says ssh is already up to date. Perhaps there is an auto update thats always updating without my knowledge?

---

### Post by zvacet on 2008-05-19
Try in terminal


```
sudo
```

and see output.It should be like this


usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...


if it is not then sudo is broken

---

### Post by kerry_s on 2008-05-19
ubuntu is a snap shot distro, once released, there will be only security updates which are few and far between. showing no updates will be the norm

---

