---
title: "Feisty version mismatch"
date: 2007-04-01
forum: General Help
---

### Post by nsilva on 2007-04-01
I started playing with Feisty today and everything went smooth...
However, something confuses me why do I have a mismatch in versions

> 
nsilva@Typhon:~$ cat /etc/issue
Ubuntu 6.06.1 LTS \n \l

nsilva@Typhon:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"
nsilva@Typhon:~$ 



Shouldnt it display the Fesity information? I'm even doubting now that I actually have Fesity, haha... well all my source.list is Feisty.:lolflag:

---

### Post by eentonig on 2007-04-01
This is what mine reads. So I seriously doubt that you are indeed runnning Feisty.

> rfonteyn@ubuntu:~$ cat /etc/issue
Ubuntu feisty (development branch) \n \l

rfonteyn@ubuntu:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu feisty (development branch)"
rfonteyn@ubuntu:~$ 


---

### Post by zvacet on 2007-04-01
How did you upgraded?Source list means nothing,because you can change it manualy.Go to the system>about Ubuntu and you will know for sure wich version do you have.

---

### Post by nsilva on 2007-04-01
Is there anyay I can check Im running 7.04, I double
check the CD ans it says Ubuntu 7.04 Fesity

---

### Post by nsilva on 2007-04-01
> **zvacet said:**
> How did you upgraded?Source list means nothing,because you can change it manualy.Go to the system>about Ubuntu and you will know for sure wich version do you have.
Thank you for your interest in Ubuntu 7.04 - the Feisty Fawn - released in April 2007.

So I guess I am using the latest version, but still Im wondering why **issue and lsb-release** have different information.

Anyone can think of the impact this might have??? or is just informative

---

### Post by bapoumba on 2007-04-01
```
~ $ lsb_release -cd
Description:    Ubuntu feisty (development branch)
Codename:       feisty
~ $ uname -a
Linux desktop 2.6.20-13-generic #2 SMP Sun Mar 25 00:21:25 UTC 2007 i686 GNU/Linux

```
Which kernel are you running on ?

---

### Post by nsilva on 2007-04-01
> **bapoumba said:**
> ```
~ $ lsb_release -cd
Description:    Ubuntu feisty (development branch)
Codename:       feisty
~ $ uname -a
Linux desktop 2.6.20-13-generic #2 SMP Sun Mar 25 00:21:25 UTC 2007 i686 GNU/Linux

```
Which kernel are you running on ?
nsilva@Oracle:~$ uname -a
Linux Oracle 2.6.20-13-generic #2 SMP Sun Mar 25 00:21:25 UTC 2007 i686 GNU/Linux
nsilva@Oracle:~$ lsb_release -cd
Description:    Ubuntu feisty (development branch)
Codename:       feisty
nsilva@Oracle:~$ 

There has to be a messed up no?

---

### Post by bapoumba on 2007-04-01
How did you get feisty ? I did a fresh install:
```
~ $ aptitude show lsb-release
Package: lsb-release
State: installed
Automatically installed: no
Version: 3.1-22ubuntu2
Priority: important
Section: misc
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Uncompressed Size: 81.9k
Depends: python
Recommends: lsb
Description: Linux Standard Base version reporting utility
 The Linux Standard Base (http://www.linuxbase.org/) is a standard core system
 that third-party applications written for Linux can depend upon. 
 
 The lsb-release command is a simple tool to help identify the Linux
 distribution being used and its compliance with the Linux Standard Base. LSB
 conformance will not be reported unless the required metapackages are
 installed. 
 
 While it is intended for use by LSB packages, this command may also be useful
 for programmatically distinguishing between a pure Debian installation and
 derived distributions.

```
My guess is that you have lsb-release from feisty (and that you are indeed running feisty) but somehow the issue and lsb-release files in /etc have not been updated. Try:
```
sudo aptitude update
sudo aptitude dist-upgrade
```
If this does not work, I am running out of ideas :/
[http://www.linux-foundation.org/en/LSB]("http://www.linux-foundation.org/en/LSB")

---

### Post by nsilva on 2007-04-03
> **bapoumba said:**
> How did you get feisty ? I did a fresh install:
```
~ $ aptitude show lsb-release
Package: lsb-release
State: installed
Automatically installed: no
Version: 3.1-22ubuntu2
Priority: important
Section: misc
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Uncompressed Size: 81.9k
Depends: python
Recommends: lsb
Description: Linux Standard Base version reporting utility
 The Linux Standard Base (http://www.linuxbase.org/) is a standard core system
 that third-party applications written for Linux can depend upon. 
 
 The lsb-release command is a simple tool to help identify the Linux
 distribution being used and its compliance with the Linux Standard Base. LSB
 conformance will not be reported unless the required metapackages are
 installed. 
 
 While it is intended for use by LSB packages, this command may also be useful
 for programmatically distinguishing between a pure Debian installation and
 derived distributions.

```
My guess is that you have lsb-release from feisty (and that you are indeed running feisty) but somehow the issue and lsb-release files in /etc have not been updated. Try:
```
sudo aptitude update
sudo aptitude dist-upgrade
```
If this does not work, I am running out of ideas :/
[http://www.linux-foundation.org/en/LSB]("http://www.linux-foundation.org/en/LSB")
I did not upgrade, it is a fresh install. I had XP on that box before. 
I did the dist-upgrade but there is no upgrade for the distro...

who knows? It really does not make a difference

---

