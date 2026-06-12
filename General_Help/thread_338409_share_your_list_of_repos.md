---
title: "share your list of repos"
date: 2007-01-14
forum: General Help
---

### Post by xGutsAndGloryx on 2007-01-14
i am looking for a good list of repositories.. i have looked all over the net and found mixed results with many different ones.. please share your list of repos

---

### Post by Jussi Kukkonen on 2007-01-14
Just a reminder: As far as security is concerned adding unknown repositories is even worse than running unknown binary installers. So you shouldn't add repositories unless
1) you really trust the people who host and modify the repository
2) You really need something from that repo

I'm sorry if I sound patronizing, but "looking for a list of repositories" sounds pretty reckless...

---

### Post by rabid9797 on 2007-01-14
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

---

### Post by xGutsAndGloryx on 2007-01-14
> **Jussi Kukkonen said:**
> Just a reminder: As far as security is concerned adding unknown repositories is even worse than running unknown binary installers. So you shouldn't add repositories unless
1) you really trust the people who host and modify the repository
2) You really need something from that repo

I'm sorry if I sound patronizing, but "looking for a list of repositories" sounds pretty reckless...

i understand.... i am still very new to linux... i am just trying to get everything configured and the best software on my system....

---

### Post by Cable on 2007-01-14
##Google Picasa
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free #Google Picasa

##Deluge
deb [http://espergreen.com/apt](http://espergreen.com/apt) edgy main #Deluge

##Wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main #Wine

##Murrine
deb [http://malteo.homelinux.net](http://malteo.homelinux.net) edgy-malteo extras

##Canonical Commercial
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

##Opera
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free

---

### Post by ardchoille42 on 2007-01-14
Just a note, the more repos you add, the more chance you have of running into problems.

My /etc/apt/sources.list is:

```

# This is the Ubuntu 6.06.1 LTS sources.list that is used by the package managers.

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

```

This may be why I have **never** had any problems in Ubuntu on more than 11 different computers ;)

---

