---
title: "Xubuntu 14.04 Can't Install Any Packages"
date: 2014-05-17
forum: General Help
---

### Post by philip19 on 2014-05-17
I've tried to install wine so I can play a few games, and I've also tried to install flash, none of these work. I've tried both from the software center and straight from terminal.
I don't really care for flash, just really want wine. Flash was mostly to test if other PPAs work. Here's what I get from terminal after trying to install wine.

user@chrubuntu:~$ sudo apt-get install wine1.7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package wine1.7
E: Couldn't find any package by regex 'wine1.7'

I've already done
sudo add-apt-repository ppa:ubuntu-wine/ppa

and
sudo apt-get update

Thanks for any help.

---

### Post by deadflowr on 2014-05-17
What is the output for
```
sudo apt-get update
```

---

### Post by ibjsb4 on 2014-05-17
Have you checked out PlayOnLinux?  I use it for older games, its a front end for wine.

[https://help.ubuntu.com/community/PlayOnLinux](https://help.ubuntu.com/community/PlayOnLinux)

---

### Post by philip19 on 2014-05-17
```
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release    
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates InRelease
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security InRelease
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty Release
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates Release                    
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security Release                   
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/main Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/restricted Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/multiverse Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/universe Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/main armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/restricted armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/multiverse armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/universe armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/main Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/multiverse Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/restricted Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/universe Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/main Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/restricted Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/multiverse Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/universe Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/main armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/restricted armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/multiverse armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/universe armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/main Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/multiverse Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/restricted Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/universe Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/main Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/restricted Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/multiverse Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/universe Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/main armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/restricted armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/multiverse armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/universe armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/main Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/multiverse Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/restricted Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/universe Translation-en
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/main i386 Packages
  404  Not Found [IP: 91.189.88.140 80]
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/restricted i386 Packages
  404  Not Found [IP: 91.189.88.140 80]
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/multiverse i386 Packages
  404  Not Found [IP: 91.189.88.140 80]
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/universe i386 Packages
  404  Not Found [IP: 91.189.88.140 80]
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/main i386 Packages
  404  Not Found [IP: 91.189.88.140 80]
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.88.140 80]
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.88.140 80]
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/universe i386 Packages
  404  Not Found [IP: 91.189.88.140 80]
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/main i386 Packages
  404  Not Found [IP: 91.189.88.140 80]
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/restricted i386 Packages
  404  Not Found [IP: 91.189.88.140 80]
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.88.140 80]
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/universe i386 Packages
  404  Not Found [IP: 91.189.88.140 80]
W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty/main/binary-i386/Packages](http://ports.ubuntu.com/ubuntu-ports/dists/trusty/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.140 80]


W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty/restricted/binary-i386/Packages](http://ports.ubuntu.com/ubuntu-ports/dists/trusty/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.88.140 80]


W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty/multiverse/binary-i386/Packages](http://ports.ubuntu.com/ubuntu-ports/dists/trusty/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.88.140 80]


W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty/universe/binary-i386/Packages](http://ports.ubuntu.com/ubuntu-ports/dists/trusty/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.88.140 80]


W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty-updates/main/binary-i386/Packages](http://ports.ubuntu.com/ubuntu-ports/dists/trusty-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.140 80]


W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty-updates/restricted/binary-i386/Packages](http://ports.ubuntu.com/ubuntu-ports/dists/trusty-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.88.140 80]


W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty-updates/multiverse/binary-i386/Packages](http://ports.ubuntu.com/ubuntu-ports/dists/trusty-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.88.140 80]


W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty-updates/universe/binary-i386/Packages](http://ports.ubuntu.com/ubuntu-ports/dists/trusty-updates/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.88.140 80]


W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty-security/main/binary-i386/Packages](http://ports.ubuntu.com/ubuntu-ports/dists/trusty-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.140 80]


W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty-security/restricted/binary-i386/Packages](http://ports.ubuntu.com/ubuntu-ports/dists/trusty-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.88.140 80]


W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty-security/multiverse/binary-i386/Packages](http://ports.ubuntu.com/ubuntu-ports/dists/trusty-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.88.140 80]


W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty-security/universe/binary-i386/Packages](http://ports.ubuntu.com/ubuntu-ports/dists/trusty-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.88.140 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by deadflowr on 2014-05-17
You need to change mirrors.
Look over this for some idea on how
[http://askubuntu.com/questions/37753/how-can-i-get-apt-to-use-a-mirror-close-to-me-or-choose-a-faster-mirror](http://askubuntu.com/questions/37753/how-can-i-get-apt-to-use-a-mirror-close-to-me-or-choose-a-faster-mirror)

I would recommend following the second answer, with the pictures.

---

### Post by philip19 on 2014-05-17
It tells me that no suitable download servers were found, and that I need to check my internet connection.

---

### Post by deadflowr on 2014-05-17
I think crouton's need a different approach to changing mirrors.
Look over this 
[http://askubuntu.com/questions/428698/chromebook-with-crouton-alternative-repository-to-ports-ubuntu-com](http://askubuntu.com/questions/428698/chromebook-with-crouton-alternative-repository-to-ports-ubuntu-com)

Aside from that, how is the network connection?

If you need help with what's what about the link, post here and tell us which parts you need help with.

---

### Post by philip19 on 2014-05-17
It's native Ubuntu (ChrUbuntu) though, does it make a difference?

---

### Post by deadflowr on 2014-05-17
I don't know what you mean by native.

---

