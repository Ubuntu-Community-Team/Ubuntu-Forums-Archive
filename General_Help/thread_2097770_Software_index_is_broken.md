---
title: "Software index is broken"
date: 2012-12-24
forum: General Help
---

### Post by father_ted on 2012-12-24
I cant open the software sources from the software centre.

In the crash report is this line which may be the root cause.

software-properties-gtk crashed with KeyError in __getitem__(): "The cache has no package named 'xserver-xorg-video-ati'

ive gone into synaptic and deleted the cached files. this hasnt helped.

this is very annoying - any ideas on how to fix it ?

---

### Post by ibjsb4 on 2012-12-24
Have you tried updating your cache?

```
sudo apt-get update
```

---

### Post by father_ted on 2012-12-24
thanks - yes

i tried :

sudo apt-get update
sudo apt-get install -f

also tried the usual clearing and reloading through synaptic.

---

### Post by ibjsb4 on 2012-12-24
This is not looking good

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=The+cache+has+no+package+&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=The+cache+has+no+package+&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by father_ted on 2012-12-24
I did gooogle it all before i tried here. It does seem like that kind of failure occurs quite frequently. damned nuisance. i was hoping someone had a quick fix for it.

---

### Post by ibjsb4 on 2012-12-24
I wonder if forcing it would do any good

[https://help.ubuntu.com/community/SynapticHowto#How_to_force_the_installation_of_a_package_version](https://help.ubuntu.com/community/SynapticHowto#How_to_force_the_installation_of_a_package_version)

---

### Post by father_ted on 2012-12-24
strange thing is - im not trying to install anything. my updates still work normally. the problem is that i cant add or maintain any ppa's through the software centre dialog anymore which is very annoying. I only keep spotify and wine uptodate through there so its not like im doing anything complicated.

ive raised a bug for it and hopefully a workaround will be provided.

---

### Post by father_ted on 2012-12-28
The easy way to replicate this is to install wine out of the software centre. 

Seems to make a nice mess of the updater and your video drivers.

---

