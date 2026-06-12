---
title: "Software and Updates stuck on refreshing cache"
date: 2020-08-08
forum: General Help
---

### Post by mickee384 on 2020-08-08
I was removing obsolete packages from Software and Updates, and on close I reloaded them and it is stuck at 100%. Anyone have the "basic" sources.list file for ubuntu 20.04? I tried creating one with the following:
```
deb http://archive.ubuntu.com/ubuntu/ focal main restricted
deb http://security.ubuntu.com/ubuntu/ focal-security main restricted
deb http://archive.ubuntu.com/ubuntu/ focal-updates main restricted
```

But the thing continues to be stuck on refresh. Future me will back up that file before modifying the packages

---

### Post by mickee384 on 2020-08-08
I rebooted and manually added my software sources in. Fixed.

---

### Post by CelticWarrior on 2020-08-08
Repositories aren't packages ;)

In "Software and Updates" users manage repositories. In then first tab - Ubuntu Software - you can enable all but source. In the second tab you can enable the Partners repository and add/remove or disable third-party repositories (PPA) (PPAs added with 'add-apt-repository' or other commands also show up here).

---

### Post by mickee384 on 2020-08-08
Thanks CelticWarrier. I think I've got some fallout here, the apt update is working now but in the software centre the installed applications is blank. Think it has to do with /etc/apt/sources.list.d but I am not sure. Does removing packages in Software & Updates also remove them from the .list.d folder too? 

So to solve this, in this case I have replaced these 2 files from Timeshift, which was created last night, so technically I SHOULD be back where I started with the 2 correct files.

---

### Post by mickee384 on 2020-08-08
so i decided to restore the whole apt folder. All is working now.

---

