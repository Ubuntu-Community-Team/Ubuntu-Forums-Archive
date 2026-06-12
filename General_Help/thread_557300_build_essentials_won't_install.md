---
title: "build essentials won't install"
date: 2007-09-22
forum: General Help
---

### Post by steventrouble on 2007-09-22
Okay, I did this:```
sudo apt-get update
sudo apt-get install build-essential
```
and the terminal responded with:  ```
The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages

```

I tried to get all the dependencies down the list, but eventually is says:```
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20.5) but 2.5-0ubuntu14 is to be installed

```

What did I do wrong?

---

### Post by por100pre1 on 2007-09-22
Try this:

```
sudo apt-get install -f
```

Which repositories do you use?

```
cat /etc/apt/sources.list
```

and post the results...

Which version of Ubuntu are you using?

---

### Post by steventrouble on 2007-09-25
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Repository? What's that?

```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.medibuntu.org/ dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

```

Oh... I have dapper stuff, yet i use feisty...

---

### Post by Maestro23 on 2007-09-25
Looks like you need universe repos enabled.

Enabling Repositories: [https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096)

---

### Post by steventrouble on 2007-09-25
Fixed it, Thank you Maestro & por100pre1

---

### Post by Maestro23 on 2007-09-25
No prob man.  Don't forget to mark this thread SOLVED.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by xMATTIAx on 2008-03-18
hi.. 
I'm trying to isntall build-essential too, because i want to program in C . I've kubuntu 7.10 and one of my friend told to me to install build-essential. I do that, but i couldn't because i found this error. 

(snapshot)

 nobody can help me? thx

---

