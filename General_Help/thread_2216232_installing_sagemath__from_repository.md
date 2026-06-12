---
title: "installing sagemath  from repository"
date: 2014-04-10
forum: General Help
---

### Post by George Heine on 2014-04-10
Hello - 
Using Ubuntu 12.04 LTS.
The launchpad site ([https://launchpad.net/~aims/+archive/sagemath](https://launchpad.net/~aims/+archive/sagemath)) gives the following instructions for installing the Ubuntu version of sage 6.0:

```
sudo add-apt-repository -y ppa:aims/sagemath
sudo apt-get update
sudo apt-get install sagemath-upstream-binary
```

The first step seemed to work:

```
$ cat /etc/apt/sources.list.d/aims-sagemath-precise.list
deb http://ppa.launchpad.net/aims/sagemath/ubuntu precise main
deb-src http://ppa.launchpad.net/aims/sagemath/ubuntu precise main

```

and there were no errors in running "apt-get update".
But the third step produced the following 

```
Package sagemath-upstream-binary is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

```
I did manage to install sage from a downloaded binary, but am curious as to what the last message means and what could have gone wrong.

Any ideas appreciated ...

---

### Post by monkeybrain20122 on 2014-04-10
I don't know, but it seems that there are more packages for Precise than for later versions of Ubuntu and one of them failed to build. So may be some dependencies required are missing? I have replaced 12.04 a year ago when 13.04 came out but I have tried the ppa once, while it did install but never updated even though the ppa's page indicated it had a newer version, so I don't know quite what happened there at least for 12.04. Anyway I have been downloading the binaries from sage instead ever since.

---

