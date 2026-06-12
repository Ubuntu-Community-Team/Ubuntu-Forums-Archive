---
title: "sources.list incomplete on new install of Ubuntu Server 12.04.2 x64"
date: 2013-03-13
forum: General Help
---

### Post by adwsys on 2013-03-13
Hi All,

I'm very new to Linux and I've just spent a very frustrating few hours trying to figure out a problem with a fresh install of Ubuntu Server 12.04.2 x64 on a HP Microserver. The install itself completed ok, once I'd figured out how to make it work from a USB flash drive, but after the system was up & running I couldn't install any software using sudo apt-get install. After much head scratching and internet searching, I discovered that the /etc/apt/sources.list file seemed to be incomplete. I used [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) to generate a sources list for the UK and 12.04 LTS and when I added these to my own sources.list file, I was then able to properly update & install the software i needed.

So my question is; Should the sources.list file not be complete with the correct entries for the installed country and version after a fresh install, or have I done something during the installation that has caused this problem. I had a fair bit of fiddling about to do to make the install run from the USB drive, but I can't see how that would have caused the problem. I've also installed 12.04 Server on a VirtualBox VM some time ago and I can't recall having any problems of this sort, so is this a bug in 12.04.2?

Andrew

---

### Post by snowpine on 2013-03-13
Hi Andrew, there is an important piece of information missing from your post, which is you failed to attach your sources.list so we can take a look for you. Without seeing your sources.list I can't even begin to speculate what went wrong. Probably you simply forgot to type "sudo apt-get update" before "sudo apt-get install" is my guess. :)

---

### Post by adwsys on 2013-03-13
Hi Snowpine,

Thanks for the response.

Here is the original sources.list file:
# deb cdrom:[Ubuntu-Server 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130214)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130214)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130214)]/ precise main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main


And these are the lines I added:

###### Ubuntu Main Repos
deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb-src [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse
deb-src [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb-src [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse

Which allowed me to get the updates & packages i needed.

I did do 'sudo apt-get update' several times before attempting to install anything, but no updates were downloaded.

Andrew

---

### Post by snowpine on 2013-03-13
The main difference I see is that you added "restricted" repos, so depending on which package you were trying to install, that is the logical explanation.

It is also possible that certain repos (UK repo in your case) will perform better on certain networks, if you have a proxy or firewall, or sometimes a certain repo might have down-time so another repo is more reliable for you... The links in your original sources.list work OK for me in the USA.

---

### Post by adwsys on 2013-03-13
The only thing I was trying to install were the webmin prerequisites, with the command line "sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl apt-show-versions python" which failed on anything that wasn't already installed.  However, it worked ok once I updated sources.list with the additional resources.  It's all working now & I've been able to install other packages without any further problems, so I was curious as to why it was like this as I like to know why things work and why they don't!

Thanks very much for your input.

Andrew

---

