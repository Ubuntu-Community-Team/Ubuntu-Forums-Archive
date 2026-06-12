---
title: "apt-get / synaptic slow!"
date: 2007-01-10
forum: General Help
---

### Post by Ampsonic on 2007-01-10
Maybe there is nothing wrong, just wanted to double check. Whenever I use apt-get or synaptic, my downloads are very slow, never above 10kb/s, usually more like 1-5kb/s, and sometimes well below. My internet connection is very fast, and when using wget with other servers I was getting above 500kb/s.

Are they just congested?

Thanks,
Nick

---

### Post by reza81 on 2007-01-10
where are you located & where does apt-get getting its sources from?

(the repositories in your sources.list)

---

### Post by taurus on 2007-01-10
Try other sites in /etc/apt/sources.list or post your /etc/apt/sources.list here.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by Ampsonic on 2007-01-10
Here is my sources.list

```
nick@nicklinux:~$ cat /etc/apt/sources.list

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

deb http://dl.ivtvdriver.org/ubuntu edgy firmware

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
# deb http://security.ubuntu.com/ubuntu edgy-security universe
deb http://archive.ubuntu.com/ubuntu/ edgy-backports restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports restricted main multiverse universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

---

### Post by Ampsonic on 2007-01-10
Also, located in Bloomington, IL, USA

---

### Post by zerhacke on 2007-01-10
I'm using the US repos too and they're at a crawl.  I've also heard the eastern Asian repos are down.  I've heard that if you remove the us. part from your sources list you use a faster repository, but I can't confirm this because I've not done this yet.

If you do edit your sources.list file, be sure to back up the old one in case something drastic happens.

---

### Post by DougieFresh4U on 2007-01-10
I live in the US as well but I took out the 'us.' and things speeded up quite a bit, my speed went from 1kb or less up to 340kb or more like where it should be

---

