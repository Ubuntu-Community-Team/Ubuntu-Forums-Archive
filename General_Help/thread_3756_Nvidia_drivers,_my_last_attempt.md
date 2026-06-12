---
title: "Nvidia drivers, my last attempt"
date: 2004-11-09
forum: General Help
---

### Post by Dennis_k on 2004-11-09
This is the last trie for me to install Nvidia drivers on Ubuntu.

I have tried everything, the wiki howto and even installing it from the nvidia website.

When i use apt-get install nvidia-glx the package is not found. I have enabeld the apt repository. dpkg -l nvidia-glx reveals nothing, there is nothing installed.

When i download the drivers from nvidia en trie to install them there is no matching module for my kernel. 

System specs:
AMD Athlon XP 2600+
Nvidia FX5700LE VTD 256
Asrock mobo

---

### Post by im_ka on 2004-11-09
it should be there. are you sure you've enabled universe and ran

```
sudo apt-get update
```

?

---

### Post by Dennis_k on 2004-11-09
Yes i've don that.

i have enabeld universe as discribed in the Howto by Ubuntu-geek.

Then i run sudo apt-get update and sudo apt-get dist-upgrade

---

### Post by ulrich on 2004-11-09
what says:
```
apt-cache search nvidia-glx
```
?
if nothing will show up, then something with your /etc/apt/sources.list is wrong.
nvidia-glx is in one of the restricted repositories.

---

### Post by Dennis_k on 2004-11-09
I will post that later today, i'm curently on my work and i have installed Ubuntu at home.

So pleasse bare with me.....

---

### Post by Slapdash on 2004-11-09
I have the same problem, not just with NVidia drivers but with other downloaded apps as well.
I cant get anything installed via apt-get or dpkg.

:(

---

### Post by im_ka on 2004-11-09
```
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 

##
## Various Multimedia Helper Apps Mplayer, Real, etc.. ##
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

#java:#
deb [http://jrfonseca.dyndns.org/debian](http://jrfonseca.dyndns.org/debian) ./
```

hope this helps

---

### Post by Dennis_k on 2004-11-09
DUDE, you have made my day happy!!

Thanks!!!!  :D  :D  :D

---

