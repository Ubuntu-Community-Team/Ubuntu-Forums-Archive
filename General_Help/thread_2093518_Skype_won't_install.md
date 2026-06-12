---
title: "Skype won't install"
date: 2012-12-11
forum: General Help
---

### Post by jaredbuck on 2012-12-11
Hi all, I am having problems installing the skype package in ubuntu.  I added the canonical partner repository like the community documentation requests, but when I try to install skype, I get the following messages:

jared@ubuntu:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype : Depends: skype-bin but it is not installable
E: Unable to correct problems, you have held broken packages.


What do I need to do to get skype installed on the computer?  it seems like something is broken but I don't know how to fix it. By the way I am using ubuntu 12.10.

Jared

---

### Post by NightsShadeQueen on 2012-12-11
What does
```
sudo apt-get install -f
```
give you?

If that fails, try
```
sudo apt-get install --reinstall skype-bin
```

---

### Post by jaredbuck on 2012-12-11
jared@ubuntu:~$ sudo apt-get install -f
[sudo] password for jared: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.
jared@ubuntu:~$ sudo apt-get install --reinstall skype-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package skype-bin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'skype-bin' has no installation candidate
jared@ubuntu:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype : Depends: skype-bin but it is not installable
E: Unable to correct problems, you have held broken packages.

Still get errors running those commands.

Jared

---

### Post by jaredbuck on 2012-12-11
[http://www.tecmint.com/install-skype-4-1-in-ubuntu-xubuntu-linux-mint/](http://www.tecmint.com/install-skype-4-1-in-ubuntu-xubuntu-linux-mint/)

A friend suggested this page, but when i try to install the 64 bit package, i get the error  package architecture (i386) does not match system (amd64)


Apparently the 64 bit package is really 32 bit.  so I guess I am stuck until skype releases a 64 bit package.

:(

Jared

---

### Post by NightsShadeQueen on 2012-12-11
Did you purge your previous install first? If you didn't, it confuses the new installation.

Looking at [http://archive.canonical.com/pool/partner/s/skype/](http://archive.canonical.com/pool/partner/s/skype/) , it seems like the 12.10 version doesn't exist yet in the ppa apt-get is searching.

---

