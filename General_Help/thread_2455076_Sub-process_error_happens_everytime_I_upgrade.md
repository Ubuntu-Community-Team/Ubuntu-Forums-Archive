---
title: "Sub-process error happens everytime I upgrade"
date: 2020-12-11
forum: General Help
---

### Post by Godspell on 2020-12-11
Hi all,

Hope everybody is keeping well.

Every time I run a system update, I get either this error ```
E: Sub-process /usr/bin/dpkg returned an error code (1)
``` or this ```
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
```.

I would then do the following and manage to run the update successfully. ```
fuser /relevant/file/path
``` ```
kill relevant_PID
``` ```
dpkg --configura -a
```

But this happens every time I run the update ever since the upgrade from 18.04 to 20.04. So I feel like something is fundamentally wrong here.

How can I find out about what's wrong and subsequently, fix it?

Thank you.

---

### Post by #&amp;thj^% on 2020-12-11
Have you then tried to fix the locked application?
```
sudo rm /var/cache/debconf/*.dat 
```
Wouldn't hurt to back that up first..(Smart)
```
sudo cp /var/cache/debconf/*.dat /var/cache/debconf/*.dat.bk
```

---

### Post by Godspell on 2020-12-11
> **1fallen said:**
> Have you then tried to fix the locked application?
```
sudo rm /var/cache/debconf/*.dat 
```
Wouldn't hurt to back that up first..(Smart)
```
sudo cp /var/cache/debconf/*.dat /var/cache/debconf/*.dat.bk
```

I have not tried to delete the config.dat file before, I can give that a go next time this happens.

But as I have said, I usually take the aforementioned steps to kill the PID locking the process and that lets me do **dpkg --configure -a** and go ahead with the update.

The question here is whether if anybody would know why this keeps happening every so often.

Furthermore, as I have explained, config.dat file is not the only culprit here. Sometimes, **/usr/bin/dpkg** is also returned with an error. And this, I'm not going to delete as it's dpkg tool itself, isn't it?

---

### Post by Impavidus on 2020-12-12
1: You can only run one package management tool at a time. If you try and run a second, it will complain about locked files. The first tool already running may be something like Software or Unattended Upgrades. Close it or wait until it finishes. Better not kill unattended-upgrades, as you'll have to fix the package manager with dpkg --configure -a.

2: If you need help with some command line tool, show us the exact command and the full output. A single line like```
E: Sub-process /usr/bin/dpkg returned an error code (1)
```doesn't really tell us more than that some error happened. We want to know what dpkg was trying to do when the error happened.

---

### Post by #&amp;thj^% on 2020-12-12
> **Godspell said:**
> I have not tried to delete the config.dat file before, I can give that a go next time this happens.

But as I have said, I usually take the aforementioned steps to kill the PID locking the process and that lets me do **dpkg --configure -a** and go ahead with the update.

The question here is whether if anybody would know why this keeps happening every so often.

Furthermore, as I have explained, config.dat file is not the only culprit here. Sometimes, **/usr/bin/dpkg** is also returned with an error. And this, I'm not going to delete as it's dpkg tool itself, isn't it?
I would never ask to do anything harmful, or that i would not do myself:
```
me@me-ThinkPad-T430:~$ sudo rm /var/cache/debconf/*.dat
me@me-ThinkPad-T430:~$ sudo apt update
Get:1 http://security.ubuntu.com/ubuntu focal-security InRelease [109 kB]
Hit:2 http://us.archive.ubuntu.com/ubuntu focal InRelease                      
Hit:3 https://repo.nordvpn.com//deb/nordvpn/debian stable InRelease            
Get:4 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]     
Hit:5 http://ppa.launchpad.net/linuxmint-tr/araclar/ubuntu focal InRelease     
Get:6 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease [101 kB]   
Fetched 324 kB in 1s (295 kB/s)   
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
```
I have a backup of course (that's just a habit i've acquired)
Just not enough supplied info to get to reason you have a locked "debconf/config.dat"
I can however appreciate your caution, but as you can see it resulted in no harm.

---

### Post by Godspell on 2020-12-15
> **Impavidus said:**
> 1: You can only run one package management tool at a time. If you try and run a second, it will complain about locked files. The first tool already running may be something like Software or Unattended Upgrades. Close it or wait until it finishes. Better not kill unattended-upgrades, as you'll have to fix the package manager with dpkg --configure -a.

2: If you need help with some command line tool, show us the exact command and the full output. A single line like```
E: Sub-process /usr/bin/dpkg returned an error code (1)
```doesn't really tell us more than that some error happened. We want to know what dpkg was trying to do when the error happened.

Fair point. In all my frustrations, I had completely overlooked that.

I'm sure it will happen again and then, I'll post the full details.

> You can only run one package management tool at a time.
This is an interesting point. I wonder if this is because there already was another (automatic) update process running in the background.
I don't have unattended-upgrades installed....unless that comes pre-installed??

Usually, I just do apt update && apt full-upgrade. And that's been working just fine..until a couple of months ago.
Anyway, I'll capture the full details next time.

Thank you.

---

### Post by Godspell on 2020-12-15
> **1fallen said:**
> I would never ask to do anything harmful, or that i would not do myself:
```
me@me-ThinkPad-T430:~$ sudo rm /var/cache/debconf/*.dat
me@me-ThinkPad-T430:~$ sudo apt update
Get:1 http://security.ubuntu.com/ubuntu focal-security InRelease [109 kB]
Hit:2 http://us.archive.ubuntu.com/ubuntu focal InRelease                      
Hit:3 https://repo.nordvpn.com//deb/nordvpn/debian stable InRelease            
Get:4 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]     
Hit:5 http://ppa.launchpad.net/linuxmint-tr/araclar/ubuntu focal InRelease     
Get:6 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease [101 kB]   
Fetched 324 kB in 1s (295 kB/s)   
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
```
I have a backup of course (that's just a habit i've acquired)
Just not enough supplied info to get to reason you have a locked "debconf/config.dat"
I can however appreciate your caution, but as you can see it resulted in no harm.

I took your advice; backed up and deleted config.dat but when I ran the update again, it threw up an error about passwords.dat and templates.dat being locked.
So, I backed up and deleted them too. Then, I ran the update again and it was fine.

---

### Post by Impavidus on 2020-12-15
> **Godspell said:**
> 
I don't have unattended-upgrades installed....unless that comes pre-installed??

It comes preinstalled. I removed it.

It's good to have a system that stays secure out of the box, but more advanced users often want to do things more manually.

---

