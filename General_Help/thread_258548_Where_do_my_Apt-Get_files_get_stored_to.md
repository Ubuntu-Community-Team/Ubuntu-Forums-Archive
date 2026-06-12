---
title: "Where do my Apt-Get files get stored to"
date: 2006-09-16
forum: General Help
---

### Post by CameronCalver on 2006-09-16
Hello i have a couple of computers and on one of them there is no internet connection so i would like to download the program of apt-get or synaptic then burn to a cd then install them onto the non internet computer.
But where are the .debs downloaded to

---

### Post by Anonii on 2006-09-16
> **CameronCalver said:**
> Hello i have a couple of computers and on one of them there is no internet connection so i would like to download the program of apt-get or synaptic then burn to a cd then install them onto the non internet computer.
But where are the .debs downloaded to
apt-get downloads and INSTALLS the programs.
You can download ths source of an application tho, burn it to a CD and pass it. Using the "apt-get source" command. For example to download the source of plotdrop, simply use:
_apt-get source plotdrop_

---

### Post by CameronCalver on 2006-09-16
so does that source command install .deb or tgz files and if i have a file on a cd do i have to do apt-get soure /media/cdrom0/....

---

### Post by Littleweseth on 2006-09-16
/var/cache/apt/archives . All downloaded pacakges live here.

There was a guide around that told you how to make your own package CD with your downloaded packages on it - I don't have the link to hand, but search the wiki. It didn't work too well for me, but i wasn't too strenuous about following the later instructions about generating public keys and whatnot.

---

### Post by ayoli on 2006-09-16
last installed deb with apt are stored in /var/cache/apt/archives/ (which must be cleaned sometimes, maybe n each reboot, i dunno)
if you want you can use it on another box and install them like this:
dpkg -i package_name
make a cd doesn't make any sense imo since there are many updates (almost once or twice a week, even everyday for compiz)

---

### Post by ayoli on 2006-09-16
> **Anonii said:**
> apt-get downloads and INSTALLS the programs.
You can download ths source of an application tho, burn it to a CD and pass it. Using the "apt-get source" command. For example to download the source of plotdrop, simply use:
_apt-get source plotdrop_

using apt-get source means compile after, if you want apt-get to download without install use:
```
apt-get -d package_name
```

---

