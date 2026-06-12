---
title: "Use Java Runtime Environment with Ubuntu Live"
date: 2005-05-25
forum: General Help
---

### Post by obonto on 2005-05-25
Hello,

i want to use the JRE with Ubuntu Live on a PPC.
Therefore I typed "sudo apt-get install java-runtime". It installed without problems, but i do not know if it is the most recent version.
If i type "java -version" it says:
ubuntu@ubuntu:~$ java -version
SableVM version 1.1.8
- compile date and time: 2005-01-01 19:44:56 UTC
- gcc version: 3.3.5 (Debian 1:3.3.5-5)
- 'real life brokenness' features enabled
- signal based exception detection
- copying garbage collection
- bidirectional object layout
- inline-threaded interpreter

Does this mean this is Java version 1.1.8? How can I install a version greater than 1.4?

obonto

---

### Post by jdong on 2005-05-25
An actual Java virtual machine is not distributed with Ubuntu or the LiveCD due to licensing restrictions imposed by Sun.
 
 
The Ubuntu Backports project does offer Sun Java 1.5.0_02 in our repos, which are installable via apt-get both on a Ubuntu installation and on the LiveCD. Note that when extracted, Java Runtime is over 90MB large, and this must fit in your RAM or any existent swap.
 
If you want to try to install it, add **deb [http://ftp2.caliu.info/backports]("http://ftp2.caliu.info/backports") hoary-extras restricted** to your /etc/apt/sources.list, then **apt-get update; apt-get install sun-j2re1.5**
 
See [http://backports.ubuntuforums.org]("http://backports.ubuntuforums.org") for more information about using Backports.

---

### Post by obonto on 2005-05-26
hello, thanks for the answer.
i added the line to my sources.list - now it looks like this:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb [http://ftp2.caliu.info/backports](http://ftp2.caliu.info/backports) hoary-extras restricted


Then i did "apt-get update".
Unfortunately, "apt-get install sun-j2re1.5" says, that the package could not be found.
Any solutions about this? (i have a Mac if this important for a solution)

obonto

---

### Post by jdong on 2005-05-26
I don't have powerpc packages for Java built. Request it at the Backports forum, and see if our in-house PPC packager will do it.

---

