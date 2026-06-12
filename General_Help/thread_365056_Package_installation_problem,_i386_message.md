---
title: "Package installation problem, i386 message"
date: 2007-02-19
forum: General Help
---

### Post by bigfootx2 on 2007-02-19
I cannot install software I need in Edgy.

Using add/remove hardware, I get this message:
AbiWord Word Processor cannot be installed on your computer type (i386)

There is a similar message for other listed packages that I tried. My processor is a P3 mobile, and I wonder if it has been incorrectly identified.

When I use sudo apt-get install abiword, the result is:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package abiword

I don't know what this means. Can anyone help?

---

### Post by useResa on 2007-02-19
> **bigfootx2 said:**
> When I use sudo apt-get install abiword, the result is:
Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: Couldn't find package abiword
 
I don't know what this means. Can anyone help?
The fact that the package could not be found mostly means that the package is not available in the repositories you are currently using.
 
Could you please post the content of your /etc/apt/sources.list here?

---

### Post by bigfootx2 on 2007-02-19
Thanks, useResa, for your interest in my problem. This is sources.list:

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by useResa on 2007-02-20
From what I see is that you only have the CD-repository and the main repository "uncommented". AFAIK you need the Universe repository for most of the Open Source software.
 
My suggestions to you is uncomment the Universe repository by removing the **#** symbol in front of the line and changing it into:
[I]deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe[/I]

Please, do NOT forget to run the following command AFTER changing your sources.list
```
sudo apt-get update
```
If my assumptions are correct you should then be able to install AbiWord.
 
BTW: More information on the repositories can be found [here](http://www.ubuntu.com/ubuntu/components) and on editing them [here](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by bigfootx2 on 2007-02-21
Changes to the file have fixed it.

Thank you for your helpful advice. Now I understand the repositories system, and I guess sources.list is the first place to look if apt-get doesn't work.

Much appreciated

bigfootx2

---

