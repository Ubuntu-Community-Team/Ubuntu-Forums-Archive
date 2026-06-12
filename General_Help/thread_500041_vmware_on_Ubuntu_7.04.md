---
title: "vmware on Ubuntu 7.04"
date: 2007-07-13
forum: General Help
---

### Post by ali780 on 2007-07-13
[SIZE="4"]Hi everybody.
I am trying to install vmware-server on my ubuntu 7.04 for using windows in my ubuntu, Bu I could not do it. I have used several diferent instruction But I had no success. Please sombody give me a step by syep instruction.
Thank you
[/SIZE]

---

### Post by TheExplorer on 2007-07-13
Dunno about vmware but I advise you to try [Virtualbox]("http://virtualbox.org/") instead. No problems for me.

---

### Post by tszanon on 2007-07-13
I don't use Feisty (I'm still on Dapper, thinking about going Edgy). But the process of installing vmware server should be the same:
1. download the latest version from [www.vmware.com;](www.vmware.com;)
2. get a serial number from the same site;
3. decompress the tarball;
4. run the installer with sudo (I don't remember, but I think it is the script vmware-install.pl);
5. the installer will ask you a lot of questions. For me, the default answers were almost always correct;
6. the installer you run the vmware-configure.pl, to configure the thing.

You'll need a C++ compiler (gcc) and the kernel-headers (I NEVER remember the name of the package :().

If you need help on some specific step, remember to post the messages you receive (if any).

---

### Post by jespdj on 2007-07-13
If you don't tell us exactly what went wrong then it will be very hard to help you solve the problem you encountered! So, what exactly did you try and what problem did you encounter?

I used the following instructions to install VMWare Server and it went without any problems (I'm using 64-bit Kubuntu 7.04):

[How to install Vmware server From Canonical commercial repository in Ubuntu Feisty](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

---

### Post by xavier_r on 2007-07-14
Check this out
[http://flac.wordpress.com/2007/07/13/vmware-workstation-for-feisty/](http://flac.wordpress.com/2007/07/13/vmware-workstation-for-feisty/)

and check the modified packages below

---

