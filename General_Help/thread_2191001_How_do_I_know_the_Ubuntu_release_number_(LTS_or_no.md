---
title: "How do I know the Ubuntu release number (LTS or not)?"
date: 2013-11-30
forum: General Help
---

### Post by ruwan2 on 2013-11-30
Hi,
I installed an Ubuntu 12 on my PC. Now an applictation software requires a Ubuntu 10.04LTS. My first question is that how can I download 10.04LTS?
Then, if 10.04LTS is not available, then 12.04LTS may be an alternative. I don't know whether my present installation release number now. I would like to check it before I install a 12.04 LTS. If I am lucky that the present installation is 12.04LTS, I do not need to reinstall it now.

Thanks,

---

### Post by Bashing-om on 2013-11-30
ruwan2; Hi !

I prefer to look at things from the terminal:
do Terminal code -release info- :
```

lsb_release -a

```
and for kernel info:
```

uname -a

```

Aside: version 10.04 no longer enjoys support for the desk top.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2013-11-30
Open a terminal and run this command

```
lsb_release -a
```

This is what I get

> No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Trusty Tahr (development branch)
Release:    14.04
Codename:    trusty

Your printout should say, Description: Precise Pangolin; Release: 12.04 LTS or 12.04.1 or 12.04.2 or 12.04.3 depending upon its age; Codename: precise.

Ubuntu 10.04 LTS desktop version is no longer supported. It is best to install software that is available through the Ubuntu Software Centre. What application do you wish to install and where are you downloading it from? If that application is suitable for Ubuntu 10.04 then it is old software. There should be a version of it for Ubuntu 12.04. If there is not a version for Ubuntu 12.04 then it may be that the software is no longer being maintained.

By the way LTS = Long Term Support. For 10.04 desktop that meant 3 years. For 12.04 desktop it means 5 years. Every two years the April release of Ubuntu is designated a Long Term Support release. The six monthly Ubuntu releases in between have a lot less support. Ubuntu 13.04 and 13.10 only have 9 months support.

Regards.

---

### Post by deadflowr on 2013-11-30
10.04LTS can be downloaded from here
[http://old-releases.ubuntu.com/releases/10.04.0/](http://old-releases.ubuntu.com/releases/10.04.0/)

Warning: This is the old-release area for Ubuntu, as such, the version in it are no longer supported and in a sense are frozen in time.
Any bugs will never get fixed.
Along with the release are also the repos for the release, so you would need to change the source.lists to reflect the old-release repos instead of the typical archive/security repos.

I do not condone or support running dead releases, except in limited ways such as to immediately upgrade from it to a supported version or in an isolated manner such as a vm,  but it is there for you to choose for yourself.

---

