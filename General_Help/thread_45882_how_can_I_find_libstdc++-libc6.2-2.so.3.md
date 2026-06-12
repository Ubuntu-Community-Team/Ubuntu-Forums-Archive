---
title: "how can I find libstdc++-libc6.2-2.so.3"
date: 2005-07-02
forum: General Help
---

### Post by ricardo06 on 2005-07-02
Hello, i am trying to run an application that ran on RH 7.3. It claims for  libstdc++-libc6.2-2.so.3. 
Is there an equivalent library under Ubuntu/Debian and most of all, where can I find it.
I tried to apt-get and it failed to find it. 
Here is my sources.lst 

[COLOR=Blue]deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted


deb-src [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
[/COLOR]


I am running Hoary / amd64

Many Thanks for your help.

Richard

---

### Post by Majlo on 2005-07-02
Look at this page [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

libstdc++-libc6.2-2.so.3 is in libstdc++2.10-glibc2.2

*sudo apt-get install libstdc++2.10-glibc2.2* 

Package is in Universe repo

---

### Post by Stemp on 2005-07-02
[http://packages.debian.org/cgi-bin/search_contents.pl?word=libstdc%2B%2B-libc6.2-2.so.3&searchmode=searchfiles&case=insensitive&version=stable&arch=i386](http://packages.debian.org/cgi-bin/search_contents.pl?word=libstdc%2B%2B-libc6.2-2.so.3&searchmode=searchfiles&case=insensitive&version=stable&arch=i386)

Hope this help...

---

### Post by ricardo06 on 2005-07-02
Thanks a lot 
I did find the package and I bookmarked the urls. 

It is strange that apt-get install do  not find the packages. I have to download and then install "by hand" . 
May be i miss something ?

Richard

---

### Post by Majlo on 2005-07-02
In your sources.list missing universe repository ..
Look at this [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

But package  libstdc++2.10-glibc2.2 is only for i386 not for amd64 ..
Is it problem ?

---

### Post by ricardo06 on 2005-07-03
I thought that line would make due for universe repository ?

[COLOR=Blue]deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse
[/COLOR]
But it is true that the packahe is i386 and when unpacking dpakg complains about not being 64 bit and it is not compatible with my machine architecture.
I read elsewhere that people set up a "chroot" to have 32 bit compatibility ? It is quite a process to set this up I hope i could avois this.
Do you have any idea ?

Richard

---

