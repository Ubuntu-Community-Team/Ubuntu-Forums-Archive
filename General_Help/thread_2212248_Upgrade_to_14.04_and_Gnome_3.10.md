---
title: "Upgrade to 14.04 and Gnome 3.10"
date: 2014-03-20
forum: General Help
---

### Post by Korkel on 2014-03-20
Hello,

I am on this moment using Ubuntu 13.10 with the Gnome 3.10 theme. When Ubuntu 14.04 comes out, can I upgrade it without losing Gnome 3.10 using the following command in a terminal:
```
sudo apt-get upgrade
```

Is there also a date the version will be released, official?

---

### Post by sudodus on 2014-03-20
You upgrade to the next level with the command

```
do-release-upgrade
```

and if it is the developing version (now Trusty Tahr), use the option -d

```
do-release-upgrade -d
```

But it is risky, so ***backup*** your system before doing it.

---

### Post by Korkel on 2014-03-20
> **sudodus said:**
> You upgrade to the next level with the command

```
do-release-upgrade
```

and if it is the developing version (now Trusty Tahr), use the option -d

```
do-release-upgrade -d
```

But it is risky, so ***backup*** your system before doing it.
I will wait until it has been released official, and how do I make a backup of my system?

---

### Post by sudodus on 2014-03-20
To be honest, wait for at least two weeks after the release, so upgrade around May 10 or later! At that time the worst bugs will be squashed and you will get a smoother ride.

There are many ways to backup a system. The basic level is to backup your personal files and maybe some configuration files to an external drive, a network drive or an internet cloud service. You can use ***Simple Backup***, ***DejaDup***, ***Redo Backup*** or the powerful command line tool ***rsync*** or ***fsarchiver***, and many other tools.

A more advanced level is to make a complete image of the system, which can be restored to a cloned copy in a new drive of at least the same size, if the old one is damaged. I do such backups seldom, typically at a new installation and when upgrading to a new version. ***Clonezilla*** is a good tool for this purpose.

---

### Post by Korkel on 2014-03-20
Thanks for the information, will Google the programs.

---

