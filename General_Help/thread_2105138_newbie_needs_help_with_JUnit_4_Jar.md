---
title: "newbie needs help with JUnit 4 Jar"
date: 2013-01-15
forum: General Help
---

### Post by Quarkrad on 2013-01-15
I'm following **[https://wiki.documentfoundation.org/Development/Linux_Build_Dependencies#Natty.2FOneric.2FPrecise](https://wiki.documentfoundation.org/Development/Linux_Build_Dependencies#Natty.2FOneric.2FPrecise)** specifically the section:
```


 Natty/Oneric/Precise

Get the dependencies:

sudo apt-get build-dep libreoffice

Get ccache:

sudo apt-get install ccache

Get git:

sudo apt-get install git-core

Get upstream Junit at https://github.com/downloads/KentBeck/junit/junit-4.9b2.jar, because of https://bugs.launchpad.net/ubuntu/+source/junit/+bug/784631. When you use autogen.sh, specify the location of Junit with:

--with-junit=<absolute path to JUnit 4 jar>

```

I have carried out the terminal commands and at the point where I have downloaded junit-4.9b2.jar and extracted the contents.  I need help with the command **--with-junit=<absolute path to JUnit 4 jar>**.  Assuming I have extracted the contents to /Downloads/ I'm not sure what the command about is telling me to do/what it is doing or more importantly, what terminal command I use.  Is it as simple as **--with-junit=~/Downloads**  ?

---

### Post by dino99 on 2013-01-15
its ready to use via that ppa :

[https://launchpad.net/~alexandre-montplaisir/+archive/ppa](https://launchpad.net/~alexandre-montplaisir/+archive/ppa)

---

