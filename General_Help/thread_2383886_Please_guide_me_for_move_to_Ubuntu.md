---
title: "Please guide me for move to Ubuntu"
date: 2018-01-30
forum: General Help
---

### Post by napra on 2018-01-30
Im already install ubuntu several times, but some issue I must back to my old os, here the guide I need from your guys 
1. Where the Installation folder for general software in ubuntu?
in my old OS => C: Program Files/installed software here
where is in ubuntu?
2. Based on my question in [https://askubuntu.com/questions/997526/why-i-cant-make-new-folder-or-paste-something-into-my-ubuntu-installation-disk](https://askubuntu.com/questions/997526/why-i-cant-make-new-folder-or-paste-something-into-my-ubuntu-installation-disk)
one comment said it is read only,
but is it normal? is it normsl if its in read only mode?
is it mean my xxxGB in that disk can't be use anymore?

---

### Post by cruzer001 on 2018-01-30
I believe your thinking is wrong.  You cannot apply your old OS (windows) ways to Linux (Ubuntu).  That will not work.

Programs will install themselves in different locations.  You see the "read only mode" because you have not used the proper command.  But again, that is not the way to do it in linux.

Tell us what program you wish to install and let us show you the proper way to install it.

Also tell us what Ubuntu and version you have installed.

---

### Post by mastablasta on 2018-01-31
java is preinstalled. if you need oracle Java you can use a PPA. i suggest this one:

[https://launchpad.net/~webupd8team/+archive/ubuntu/java](https://launchpad.net/~webupd8team/+archive/ubuntu/java)

do not mess with system folders unless you know exactly what you are doing. think twice before doing anything that needs sudo command (admin privileges)

---

### Post by HermanAB on 2018-01-31
To answer your first question:
Programs provided by your Linux distribution are installed in /bin and /usr/bin
Some programs with a BSD origin, are installed in /opt
If you compile a program from source, then it should be installed in /usr/local/bin
Libraries are in /lib and /usr/lib

The above ensures that you can have multiple versions of the same program and if you update your distribution, then it will not overwrite a program that you compiled from source or got from BSD.

---

### Post by napra on 2018-02-04
thanks for all people who replying to my thread, I'm really appreciate it :)
Im planing to installing ubuntu again if I really get answer or guide, and this time i planing to use ubuntu 17.

im worrying about "read only mode" because I put in that disk a huge space disk size, about 150gb, so I think im wasting my 150gb of my hadrdisk.
So, do I need make 150gb for ubuntu installation file like my local C in my windows? or just make it like max 10gb for ubuntu os only?

---

### Post by cruzer001 on 2018-02-04
Here's some helpful links

[https://help.ubuntu.com/stable/ubuntu-help/index.html](https://help.ubuntu.com/stable/ubuntu-help/index.html)

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

[https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#0](https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#0)

---

### Post by litlesam on 2018-02-05
Hi, Do you really need Ubuntu 17.1 it has a short life. Would recommend 16.04 LTS which is good till April 2021.
Ubuntu 18.04 LTS will be released in April of this year but I would wait for 6 months before installing it.
Any version ending LTS is a Long Term Support good for up to 5 years.

If your equipment will work with 16.04 LTS, that's where I would stay. :)

---

### Post by mastablasta on 2018-02-05
> **napra said:**
> 
im worrying about "read only mode" because I put in that disk a huge space disk size, about 150gb, so I think im wasting my 150gb of my hadrdisk.
So, do I need make 150gb for ubuntu installation file like my local C in my windows? or just make it like max 10gb for ubuntu os only?

only the directory (folder in windows speak) is read only, not the disk. malware, therefore needs your permission to run there. it's a security layer and as i know windows does the same nowadays.

bypass is with sudo command (read this first! : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo))

you can unpack and run the file in your /home folder. do not use the root (/) and system folders for file extractions etc. you can do that in home folder. and if something needs sudo to run, think and make sure you really want to run as sudo, before you do it.

---

