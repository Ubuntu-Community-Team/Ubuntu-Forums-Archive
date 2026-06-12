---
title: "Thunderbird update"
date: 2005-08-29
forum: General Help
---

### Post by garak on 2005-08-29
I see on security announcements that last release of mozilla thunderbird is 1.0.6-0ubuntu05.04
But I can't see it on my synaptic, even if my repositories are up to date: last version I see is 1.0.2

Am I missing something? :|

---

### Post by arnieboy on 2005-08-29
[QUOTE=garak]I see on security announcements that last release of mozilla thunderbird is 1.0.6-0ubuntu05.04
But I can't see it on my synaptic, even if my repositories are up to date: last version I see is 1.0.2

Am I missing something? :|[/QUOTE]
do u have the backports enabled in ur apt repositories?
[http://ubuntuguide.org#repositories](http://ubuntuguide.org#repositories)

---

### Post by garak on 2005-08-30
[QUOTE=arnieboy]do u have the backports enabled in ur apt repositories?
[http://ubuntuguide.org#repositories]("http://ubuntuguide.org#repositories")[/QUOTE]

I think so

 ```
grep -v '#' /etc/apt/sources.list

deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary-updates main restricted
deb http://archive.ubuntu.com/ubuntu/ hoary universe main restricted multiverse
deb http://ubuntu.tower-net.de/ubuntu/ hoary java
deb http://ubuntu-backports.mirrormax.net/ hoary-backports bleeding main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras bleeding main universe multiverse restricted

```

---

### Post by arnieboy on 2005-08-30
[QUOTE=garak]I think so

 ```
grep -v '#' /etc/apt/sources.list

deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary-updates main restricted
deb http://archive.ubuntu.com/ubuntu/ hoary universe main restricted multiverse
deb http://ubuntu.tower-net.de/ubuntu/ hoary java
deb http://ubuntu-backports.mirrormax.net/ hoary-backports bleeding main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras bleeding main universe multiverse restricted

```[/QUOTE]
make your /etc/apt/sources.list look like the following:
```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

### Post by yhotg on 2005-08-30
hi.
i had thunderbird 1.0.6  installed from the apt but it couldn't make updates of the extentions
so i went back to the package from the mozilla site

i think it works a little better, faster. but i don't really know that. only that i can update extentions and themes without problems.

hope it helped.

yhotg

---

### Post by bionnaki on 2005-08-30
yeah, installing firefox/thunderbird is easy...I just download the updates via mozilla.org & install.

---

### Post by garak on 2005-08-31
[QUOTE=arnieboy]make your /etc/apt/sources.list look like the following:[/QUOTE]
Ok, the matter was I commented the security repositories ](*,)
Thanks a lot! :)

---

