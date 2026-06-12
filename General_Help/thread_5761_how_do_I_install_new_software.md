---
title: "how do I install new software ?"
date: 2004-11-22
forum: General Help
---

### Post by ubuntu_demon on 2004-11-22
Hi,

I'm working in my ubuntu live-cd.

sudo apt-get update

gives :

Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Packages [51.7kB]
E: Method http has died unexpectedly!

my sources.list :

```

deb http://archive.ubuntu.com/ubuntu/ warty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ warty universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ warty universe multiverse

deb http://security.ubuntu.com/ubuntu/ warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted

```

---

### Post by arctic on 2004-11-22
if you use the live-cd and have not done a hard-disk install, i guess it is pretty useless to run apt-get... where should any files be saved and installed to if apt-get cannot write to the cd (which is not a cdrw)?

---

### Post by ubuntu_demon on 2004-11-22
I want to try getting my VIA raid VT6410 chip to work. I don't want to install ubuntu on this pc if I can't get it to work. (I want to be able to see the striping raid array I use in windows XP)

---

### Post by ubuntu_demon on 2004-11-22
I changed my mind and I decided to install ubuntu in a dual boot config with windows XP. I'm now running ubuntu on my P4.

---

