---
title: "Cann't install 32 bit packages in Ubuntu 64 Bit"
date: 2014-07-13
forum: General Help
---

### Post by Linuxour on 2014-07-13
Hello,

I've Ubuntu 14.04 64-Bit. I've been trying to install "libqt3support4-perl:i386" for a while and I cann't. I searched for answers on google and tried many things but in vain. What I tried

1
```
sudo apt-get install libc6-i386 libglib2.0-0:i386 libsm6:i386 \
libglu1-mesa:i386 libgl1-mesa-glx:i386 libxext6:i386 \
libxrender1:i386 libx11-6:i386 libfontconfig1:i386 lsb-core

```
2
```
sudo -i
cd /etc/apt/sources.list.d
echo "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring main restricted universe multiverse" >ia32-libs-raring.list
apt-get update
apt-get install ia32-libs
rm /etc/apt/sources.list.d/ia32-libs-raring.list
apt-get update

```
3
```
sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386

```



When I try to install "libqt3support4-perl:i386" from software center I get

===
Package dependencies cannot be resolved


This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
The following packages have unmet dependencies:


libqt3support4-perl:i386: Depends: libqtcore4-perl (= 4:4.13.0-0ubuntu1) but 4:4.13.0-0ubuntu1 is to be installed
                          Depends: libqtgui4-perl (= 4:4.13.0-0ubuntu1) but 4:4.13.0-0ubuntu1 is to be installed
                          Depends: libqtnetwork4-perl (= 4:4.13.0-0ubuntu1) but 4:4.13.0-0ubuntu1 is to be installed
                          Depends: libqtsql4-perl (= 4:4.13.0-0ubuntu1) but 4:4.13.0-0ubuntu1 is to be installed
                          Depends: perlapi-5.18.2 but it is a virtual package


====


Could you please tell me what should I do ?

---

### Post by oldos2er on 2014-07-13
You say 14.04, but raring (13.04) hasn't been supported since January, so its repositories are offline. This could explain the error you're seeing. If you're really running 14.04, I'd remove any raring repositories.

---

### Post by Linuxour on 2014-07-14
Thank you. I removed it. But I still have the problem.

---

