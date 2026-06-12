---
title: "Installing STAR"
date: 2013-10-23
forum: General Help
---

### Post by RH3dDbz on 2013-10-23
Hello, I have Ubuntu Client LTS version 12.04, I want to install a program called "star", I search on Ubuntu Software Center, but I do not find, and try with the command apt-get install star, and I do not find the program, I found a example how to use the program here is the link: 

[https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Security-Enhanced_Linux/sect-Security-Enhanced_Linux-Maintaining_SELinux_Labels_-Archiving_Files_with_star.html](https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Security-Enhanced_Linux/sect-Security-Enhanced_Linux-Maintaining_SELinux_Labels_-Archiving_Files_with_star.html)

STAR – Unique Standard Tape Archiver
The tool star is a command backups very fast like tar, with more features.

 Can I install on Ubuntu Client LTS version 12.04?, please if somebody can help me, thanks in advance.

---

### Post by ibjsb4 on 2013-10-23
Your on a RedHat site, a Fedora site.  

[http://fedoraproject.org/](http://fedoraproject.org/)

RedHat uses 'yum' packages and Ubuntu uses 'deb' packages.

---

### Post by RH3dDbz on 2013-10-23
Hello ibjsb4, thank you for replying, I need this tool, I'm taking a course about Linux, and the teacher give me a homework whiere I have to use this command.

---

### Post by RH3dDbz on 2013-10-23
It means I have to change from Ubuntu to Fedora or Red Hat. :(

---

### Post by Habitual on 2013-10-23
install RH/Fedora in Virtualbox
yum install star

---

### Post by mörgæs on 2013-10-23
Please use a more descriptive thread title.
Changed.

---

### Post by coldraven on 2013-10-23
Some packages can be converted from rpm to deb with a utility called "alien". I do not know if it will work with STAR
[http://en.wikipedia.org/wiki/Alien_%28software%29](http://en.wikipedia.org/wiki/Alien_%28software%29)
[http://joeyh.name/code/alien/](http://joeyh.name/code/alien/)
```
sudo apt-get install alien
```

---

### Post by RH3dDbz on 2013-10-23
Hello Habitual, mörgæs, coldraven, thank you for replying, I've been using Ubuntu from version 7 until now and it would be very sad to change to another distribution, looking around among my stuff I found an old computer with 1 Giga byte RAM memory, I'm going to try to install Fedora in this old computer, this way I won't need to uninstall Ubuntu.

---

### Post by tgalati4 on 2013-10-23
I'm showing that it is available on Ubuntu 9.04:


tgalati4@tpad-Gloria7 ~ $ apt-cache search   Tape Archiver
amanda-client - Advanced Maryland Automatic Network Disk Archiver (Client)
amanda-server - Advanced Maryland Automatic Network Disk Archiver (Server)
flexbackup - Flexible backup tool for small to medium sized installations
**star - A fast POSIX-compliant tape archiver**

---

### Post by RH3dDbz on 2013-11-04
Hello tgalati4, thank you for replying, I solved the problem, I install Fedora in another computer and then I can install star.

---

