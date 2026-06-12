---
title: "Where is the list of package DEB URLs located..?"
date: 2013-05-29
forum: General Help
---

### Post by KingNeil on 2013-05-29
I am using Ubuntu 12.04

According to

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

> 
As a front-end to apt, Synaptic uses the system-wide list of software repositories file located at

    /etc/apt/sources.list 


And... my "sources.list" contains

> 
# /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse


But.. I would like to know... where is the list of DEBs...

OK... In Synaptic... I can go to File > Generate package download script

And it will generate a list of DEB URLs....

For example... if I checked the box for "php5", and generated the URLs... it would give me a file with...

> 
wget -c [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5_5.3.10-1ubuntu3.6_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5_5.3.10-1ubuntu3.6_all.deb)


And so... I want to know which file Synaptic is getting this information from...

**Where is the local list of DEB file URLs...?**

Thanks

---

### Post by Cheesemill on 2013-05-29
Check the contents of these files...
```
ls -lh /var/lib/apt/lists/*Packages
```

The 'Filename:' line is appended to the base URL of the repository which can be found in your sources.list file.

---

### Post by gifford on 2013-05-29
I'm not sure if I completely understand your question. As for the local list of Deb URLs, a list a sources is /etc/apt/sources.list.d

---

### Post by HiImTye on 2013-05-29
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
```
apt-cache policy packageOrPackages
```

---

### Post by ajgreeny on 2013-05-29
As you may have now gathered synaptic gets its info on the .deb packages from the lists which you can find in /var/lib/apt/lists, with one list of .debs for each repository in your sources.list file.

All the info on each .deb file is shown in those lists.

---

