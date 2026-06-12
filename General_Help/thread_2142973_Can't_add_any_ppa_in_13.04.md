---
title: "Can't add any ppa in 13.04"
date: 2013-05-07
forum: General Help
---

### Post by cerda on 2013-05-07
Hello uforums!!

I've made a clean install of 13.04 and just can't add any ppa I try. The output is always the same, something about my internet connection (that works fine with anything else). Heres an example (sorry my instalation is in portuguese)

```
sudo add-apt-repository ppa:ehoover/compholio 
[sudo] password for andre: 
Não foi possível obter informações do PPA (https://launchpad.net/api/1.0/~ehoover/+archive/compholio), por favor verifique sua conexão com a internet.
andre@sapienz:~$ sudo add-apt-repository ppa:cooperjona/lightread
Não foi possível obter informações do PPA (https://launchpad.net/api/1.0/~cooperjona/+archive/lightread), por favor verifique sua conexão com a internet.
```

A possible translation would be "It was not possible to obtain information from the PPA, please verify you internet connection."

I don't know what could be doing this, and I really need to install some apps like netflix and lightread to make this installation worthy. Thank you

---

### Post by Frogs Hair on 2013-05-07
I looks like there is a 13.04 package for the first ppa so you may want to try changing servers in Software & Updates.

---

### Post by ibjsb4 on 2013-05-07
When I do:
```
sudo add-apt-repository ppa:ehoover/compholio
```

I get:

[https://launchpad.net/~ehoover/+archive/compholio](https://launchpad.net/~ehoover/+archive/compholio)

And you get directed to:

[https://launchpad.net/api/1.0/~ehoover/+archive/compholio](https://launchpad.net/api/1.0/~ehoover/+archive/compholio)

A bad source.  Don't know why that is.

---

### Post by amadeusrm on 2013-05-07
Same problem...
Maybe it's a bug in the 13.04 Portuguese version.

---

### Post by cerda on 2013-05-07
Any idea how can we fix this ?? It's really annoying and i'm starting to think that i can't download ubuntu updates too !!

---

### Post by EdoubleDee on 2013-05-28
I have a similar problem, but my ubuntu updates are working fine i think, as i can install packages without problems and apt-get update gives no errors, but when i

```
sudo add-apt-repository ppa:webupd8team/y-ppa-manager
```

or *any other PPA* i get

```
erik_ubuntu@Erik-MacBookAir:~$ sudo add-apt-repository ppa:webupd8team/y-ppa-manager
Cannot access PPA (https://launchpad.net/api/1.0/~webupd8team/+archive/y-ppa-manager) to get PPA information, please check your internet connection.
```

As i´m able to post this, my internet is working fine and i´m on ubuntu 13.04

---

