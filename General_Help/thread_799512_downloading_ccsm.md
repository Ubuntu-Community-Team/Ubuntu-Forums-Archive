---
title: "downloading ccsm"
date: 2008-05-19
forum: General Help
---

### Post by DaF101 on 2008-05-19
Hello everyone

I have installed ubuntu studio onto one of my computers at home and it does not have an internet connection. 

I need to download ccsm and put it onto a thum drive and then install it.

If anyone can give me a link on where to get it that would be great :)

Cheers
DaF101

---

### Post by russo.mic on 2008-05-19
Well,  you'll have to download all the dependencies as well.  There isn't really one link to download it and all the dependencies. do you have access to a computer running linux that is on the internet?  or could you boot up linux on a live CD with a computer that has an internet connection?  you could pull a 

sudo apt-get --download-only install ccsm

that would download the packages and you could then copy all of them to a thumb. they end up in /var/cache/apt/archives.  Then, pop that baby into ubuntu studio, and pull a sudo dpkg -i *.deb in the directory where you've kept the debs.  Make sure if you go the live CD route that you pull a sudo apt-get update first, or else you won't be able to find ccsm in the repos.  Good Luck!

Russo

---

### Post by Forlong on 2008-05-19
```
$ apt-cache depends compizconfig-settings-manager 
compizconfig-settings-manager
  Depends: python
  Depends: python-central
  Depends: python-compizconfig
  Depends: python-gtk2
```
Try downloading only **compizconfig-settings-manager** and **python-compizconfig**

You can do that here: [http://packages.ubuntu.com](http://packages.ubuntu.com)
Unfortunately, it seems to be down atm. But if it's back, just search for those packages and at the bottom of the page, there should be an option do download the respective package.

---

### Post by DaF101 on 2008-05-19
So what if the computer has dial up?

Is there a way to get it to work through the live CD with dial up?

If not, I might be able to do it at tafe through a virtual machine.

---

### Post by DaF101 on 2008-05-19
I did the command that you told me to do russo, but this is exackly what happend within my terminal

matt@ubuntu:~$ sudo apt-get --download-only install ccsm
[sudo] password for matt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ccsm

Do you know where it went wrong?

---

### Post by Forlong on 2008-05-20
There is no package called ccsm, it's **compizconfig-settings-manager**

---

