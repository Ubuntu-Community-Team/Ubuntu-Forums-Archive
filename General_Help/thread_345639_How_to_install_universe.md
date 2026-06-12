---
title: "How to install universe"
date: 2007-01-24
forum: General Help
---

### Post by axrh on 2007-01-24
Hi guys.  I'm having some problems installing things like nmap.  I get an error that looks like this:
axel@ubuntu:~/Desktop/nmap-4.20$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.


I think that if I install universe I can probably fix this.  How do I install universe?

thanks,
axrh

---

### Post by matthewstory on 2007-01-24
i'm pretty sure nmap is in the repositories  . . . if it is in the universal repository:

sudo gedit /etc/apt/sources.list

uncomment the universe lines . . . then:

sudo apt-get update
sudo aptitude update

sudo aptitude install nmap

good luck

---

### Post by axrh on 2007-01-24
Yup, it is.  I actually just found how to get universe going a mintue before you posted.

---

