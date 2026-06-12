---
title: "How to install KeePassX from 'source code tarball'"
date: 2016-04-15
forum: General Help
---

### Post by parker-hugh on 2016-04-15
I would like to install KeePassX on my DELL Inspiron 5559 laptop where I've recently installed Ubuntu.  I have read good reviews of this software and it is open source which is why I prefer it to the other non-free software out there.

Although I couldn't find it in the Software Manager utility, I believe KeePassX is in the repository but the version is very old, version 0.4.3 versus current version 2.0.2.  The old version only supports database version .kbd and can't open the new database version .kbdx

I couldn't find any official PPA, and I'm not keen on installing from an unofficial PPA since I'm not sure if it would be wise considering the type of software this is and maybe I would get problems in the future.

When I look on [https://www.keepassx.org/downloads/](https://www.keepassx.org/downloads/) I see there is a download available called 'Source code tarball v2.0.2'.  

So I downloaded the file which is called 'keepassx-2.0.2.tar.gz'.  The only problem is I'm not all that experienced in Linux so don't know how to install this type of package.

I understand that I should change to the directory where source code tarball has been saved in and unpack it using...
```
tar xzvf KeePassX-{version}.tar.gz
```
... but I'm not sure what I need to do next.  I don't know the correct syntax to make and install for Ubuntu installation.

Can anyone advise me how I can do this?  Any help would be appreciated.

---

### Post by howefield on 2016-04-15
What version of Ubuntu are you using ?

Inside the tarball you'll find a README.md file which explains how to install.

---

### Post by parker-hugh on 2016-04-15
> **howefield said:**
> What version of Ubuntu are you using ?

Inside the tarball you'll find a README.md file which explains how to install.
Thanks for quick reply, I'm using Ubuntu 16.04-beta2

---

### Post by howefield on 2016-04-15
Then you should have 2.0.2 available in the repositories.

I asked because I am using the xenial package in 15.10 install as well as in 16.04 installs.

```
Package keepassx

precise (12.04LTS) (utils): Cross Platform Password Manager [universe] 
0.4.3-1ubuntu2.1 [security]: amd64 i386
precise-updates (utils): Cross Platform Password Manager [universe] 
0.4.3-1ubuntu2.1: amd64 i386
trusty (14.04LTS) (utils): Cross Platform Password Manager [universe] 
0.4.3+dfsg-0.1ubuntu1.14.04.1 [security]: amd64 i386
trusty-updates (utils): Cross Platform Password Manager [universe] 
0.4.3+dfsg-0.1ubuntu1.14.04.1: amd64 i386
vivid (utils): Cross Platform Password Manager [universe] 
0.4.3+dfsg-0.1ubuntu1.15.04.2 [security]: amd64 i386
vivid-updates (utils): Cross Platform Password Manager [universe] 
0.4.3+dfsg-0.1ubuntu1.15.04.2: amd64 i386
wily (utils): Cross Platform Password Manager [universe] 
0.4.3+dfsg-0.1ubuntu1.15.10.2 [security]: amd64 i386
wily-updates (utils): Cross Platform Password Manager [universe] 
0.4.3+dfsg-0.1ubuntu1.15.10.2: amd64 i386
xenial (utils): Cross Platform Password Manager [universe] 
2.0.2-1: amd64 i386
```

---

### Post by parker-hugh on 2016-04-15
> **howefield said:**
> What version of Ubuntu are you using ?

Inside the tarball you'll find a README.md file which explains how to install.
Thanks for quick reply, I'm using Ubuntu 16.04-beta2

**EDIT: **I have found this website  [http://packages.ubuntu.com/xenial/amd64/keepassx/download](http://packages.ubuntu.com/xenial/amd64/keepassx/download) it looks like  an official ubuntu website and it seems that if I add an extra line to  my /etc/apt/sources.list 

```
deb http://cz.archive.ubuntu.com/ubuntu xenial main universe 
```
 
... then can I just install using sudo apt-get install keepassx to install the latest version 2.0.2, is this correct? 

Would this be the safest way to install this type of software so i can get updates as they become available?

---

### Post by howefield on 2016-04-15
No, just do

```
sudo apt update
```
```
sudo apt install keepassx
```

Before you install you can check the version with..

```
apt show keepassx
```

---

### Post by parker-hugh on 2016-04-15
> **howefield said:**
> Then you should have 2.0.2 available in the repositories. 
Thanks for reply, so I can just install using
```
sudo apt-get install keepassx
```
... since I didn't see it in the software manager application

---

### Post by parker-hugh on 2016-04-15
> **howefield said:**
> No, just do

```
sudo apt update
```
```
sudo apt install keepassx
```

Before you install you can check the version with..

```
apt show keepassx
```
OK I'll try that now, many thanks for your help! Much appreciated.

EDIT: I did as you suggested and it worked great. So thanks for your help and guidance, it is much appreciated.  I ran apt show keepassx before and it did confirm what you said, version is 2.0.2-1.

---

### Post by howefield on 2016-04-15
> **parker-hugh said:**
> Thanks for reply, so I can just install using
```
sudo apt-get install keepassx
```
... since I didn't see it in the software manager application

If you are using 16.04, yes you can.

Use the command above to check the version available to you, which should be something like..

```
hugh@wily-laptop:~$  apt show keepassx
Package: keepassx
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 1,882 kB
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Version: 2.0.2-1
Depends: libc6 (>= 2.14), libgcrypt20 (>= 1.6.1), libqtcore4 (>= 4:4.8.0), libqtgui4 (>= 4:4.8.0), libstdc++6 (>= 4.1.1), libx11-6, libxi6, libxtst6, zlib1g (>= 1:1.1.4)
Original-Maintainer: Reinhard Tartler <siretart@tauware.de>
Homepage: https://www.keepassx.org/
Download-Size: unknown
APT-Manual-Installed: yes
APT-Sources: /var/lib/dpkg/status
Description: Cross Platform Password Manager
 KeePassX is a free/open-source password manager or safe which helps you
 to manage your passwords in a secure way. You can put all your
 passwords in one database, which is locked with one master key or a
 key-disk. So you only have to remember one single master password or
 insert the key-disk to unlock the whole database. The databases are
 encrypted using the algorithms AES or Twofish.
```

---

