---
title: "Error when starting Adept"
date: 2007-01-04
forum: General Help
---

### Post by TheMatt on 2007-01-04
Hi. I have a small problem with Adept. Today, when doing a routine upgrade/update of my programs, adept gave me an error while installing new packages. It was something to the effect of "Sources could not accessed" or something saying it could not read the repositories. I opened Adept up again, and it gave me this message:
```
You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.
```
I tried looking for the processes in the process table with no luck and I tried this:
```
mattmodica@Stargate:~$ sudo killall apt-get
Password:
apt-get: no process killed
mattmodica@Stargate:~$ sudo killall aptitude
aptitude: no process killed
```
Both have had no success. I am not sure what to do from here. Thanks in advance for any help.

---

### Post by taurus on 2007-01-04
What about

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by TheMatt on 2007-01-04
Wow, that was fast. And it worked. Thanks!

EDIT: Some packages need the Kubuntu Edgy Eft 6.10 CD to be upgraded (that must have been why it stopped), but I only have the 6.06 Dapper CD that I upgraded from. Is there some way to use the online repositories to upgrade these packages without burning a CD?

---

### Post by taurus on 2007-01-04
You probably have to comment out the line for the CD in /etc/apt/sources.list by placing a # in front of it.  It's usually either the first line or second or somewhere near the top of the file...

```
kdesu kate /etc/apt/sources.list
```

---

### Post by TheMatt on 2007-01-04
Thanks. I did that and it looked for it on the internet, but when installing it gave me the error I was originally referring to in my first post.
```
There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages.
```
I'm not sure if it installed correctly.

---

### Post by taurus on 2007-01-04
Let's have a look at your /etc/apt/sources.list then!

```
cat /etc/apt/sources.list
```

And you said that you upgraded from Dapper to Edgy!

---

### Post by TheMatt on 2007-01-07
Sorry it took so long to get back. Here are the results:
```
## Uncomment the following two lines to fetch updated software from the network
##deb cdrom:[Kubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted
##deb cdrom:[Kubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
 deb http://archive.ubuntu.com/ubuntu edgy main restricted
 deb-src http://archive.ubuntu.com/ubuntu edgy main restricted
 ## Uncomment the following two lines to fetch major bug fix updates produced
 ## after the final release of the distribution.
 deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted
 deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted
 ## Uncomment the following two lines to add software from the 'universe'
 ## repository.
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 ## team, and may not be under a free licence. Please satisfy yourself as to
 ## your rights to use the software. Also, please note that software in
 ## universe WILL NOT receive any review or updates from the Ubuntu security
 ## team.
 deb http://archive.ubuntu.com/ubuntu edgy universe
 deb-src http://archive.ubuntu.com/ubuntu edgy universe
 deb http://security.ubuntu.com/ubuntu edgy-security main restricted
 deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
 deb http://security.ubuntu.com/ubuntu edgy-security universe
 deb-src http://security.ubuntu.com/ubuntu edgy-security universe
 deb http://archive.ubuntu.com/ubuntu edgy multiverse
 deb-src http://archive.ubuntu.com/ubuntu edgy multiverse
 deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
 deb http://archive.canonical.com/ubuntu edgy-commercial main
 deb http://packages.freecontrib.org/plf/ edgy free non-free
 deb-src http://packages.freecontrib.org/plf/ edgy free non-free



deb http://www.getautomatix.com/apt edgy main

#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END
```

---

### Post by arnieboy on 2007-01-07
Delete or comment out the following lines in your sources.list
>  deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) edgy free non-free
 deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) edgy free non-free
and do a
sudo apt-get update

---

### Post by TheMatt on 2007-01-07
I did that. Then I reinstalled a program as a test because it was giving me trouble. Then, Adept gave me the same message I was describing in my original post and shut down. Every time I follow the steps to fix it, the same thing happens, so I am stuck in a loop here.

---

