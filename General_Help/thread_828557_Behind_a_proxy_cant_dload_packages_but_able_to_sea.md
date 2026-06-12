---
title: "Behind a proxy cant dload packages but able to search"
date: 2008-06-13
forum: General Help
---

### Post by f4k1r on 2008-06-13
I am behind a college proxy..Ive done the settings in network proxy as well as in synaptic.I am able to search for packages using synaptic but not able to download.It gives 403 error.I'm new to ubuntu and using 8.04.Please help me out...:confused::confused:

---

### Post by f4k1r on 2008-06-14
BTW our university uses sonic wall firewall with squid proxy..can someone help me out?? i can access repositories through a browser so they are not blocked.

---

### Post by iaculallad on 2008-06-14
Had you tried running the commands on your terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by f4k1r on 2008-06-14
its gives failed to fetch url:// 403 forbidden.
i cant find apt.conf lol

---

### Post by iaculallad on 2008-06-14
Try posting your /etc/apt/sources.list file.

```
cat /etc/apt/sources.list
```

---

### Post by f4k1r on 2008-06-14
> **iaculallad said:**
> Try posting your /etc/apt/sources.list file.

```
cat /etc/apt/sources.list
```

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirror.lupaworld.com/ubuntu/archive/](http://mirror.lupaworld.com/ubuntu/archive/) hardy main restricted
deb-src [http://mirror.lupaworld.com/ubuntu/archive/](http://mirror.lupaworld.com/ubuntu/archive/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.lupaworld.com/ubuntu/archive/](http://mirror.lupaworld.com/ubuntu/archive/) hardy-updates main restricted
deb-src [http://mirror.lupaworld.com/ubuntu/archive/](http://mirror.lupaworld.com/ubuntu/archive/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://mirror.lupaworld.com/ubuntu/archive/](http://mirror.lupaworld.com/ubuntu/archive/) hardy universe
deb-src [http://mirror.lupaworld.com/ubuntu/archive/](http://mirror.lupaworld.com/ubuntu/archive/) hardy universe
deb [http://mirror.lupaworld.com/ubuntu/archive/](http://mirror.lupaworld.com/ubuntu/archive/) hardy-updates universe
deb-src [http://mirror.lupaworld.com/ubuntu/archive/](http://mirror.lupaworld.com/ubuntu/archive/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.lupaworld.com/ubuntu/archive/](http://mirror.lupaworld.com/ubuntu/archive/) hardy multiverse
deb-src [http://mirror.lupaworld.com/ubuntu/archive/](http://mirror.lupaworld.com/ubuntu/archive/) hardy multiverse
deb [http://mirror.lupaworld.com/ubuntu/archive/](http://mirror.lupaworld.com/ubuntu/archive/) hardy-updates multiverse
deb-src [http://mirror.lupaworld.com/ubuntu/archive/](http://mirror.lupaworld.com/ubuntu/archive/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gn.archive.ubuntu.com/ubuntu/](http://gn.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://gn.archive.ubuntu.com/ubuntu/](http://gn.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://mirror.lupaworld.com/ubuntu/archive/](http://mirror.lupaworld.com/ubuntu/archive/) hardy-security main restricted
deb-src [http://mirror.lupaworld.com/ubuntu/archive/](http://mirror.lupaworld.com/ubuntu/archive/) hardy-security main restricted
deb [http://mirror.lupaworld.com/ubuntu/archive/](http://mirror.lupaworld.com/ubuntu/archive/) hardy-security universe
deb-src [http://mirror.lupaworld.com/ubuntu/archive/](http://mirror.lupaworld.com/ubuntu/archive/) hardy-security universe
deb [http://mirror.lupaworld.com/ubuntu/archive/](http://mirror.lupaworld.com/ubuntu/archive/) hardy-security multiverse
deb-src [http://mirror.lupaworld.com/ubuntu/archive/](http://mirror.lupaworld.com/ubuntu/archive/) hardy-security multiverse


Isnt there a file like yum.conf in YellowDog Modifier in apt??

I'm new to ubuntu:(

---

### Post by iaculallad on 2008-06-14
Sources.list look good. Try changing your Download server from System->Administration->Software Sources, on the "Ubuntu Software" tab, change "Download From" to "Main Server" and click on close button. Re-do the update in your terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by f4k1r on 2008-06-14
> **iaculallad said:**
> Sources.list look good. Try changing your Download server from System->Administration->Software Sources, on the "Ubuntu Software" tab, change "Download From" to "Main Server" and click on close button. Re-do the update in your terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

still the same problem.:mad:
do i have to use a apt.conf file from the examples and do some changes to work from behind a proxy??

---

### Post by iaculallad on 2008-06-14
This may be a long shot, but let's try FTP request instead:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

Edit the sources.list file:

```
gksudo /etc/apt/sources.list
```

and try to change all http to ftp instead (Only on uncommented lines - those without #). Save and close then retry your update.

---

### Post by f4k1r on 2008-06-14
> **iaculallad said:**
> This may be a long shot, but let's try FTP request instead:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

Edit the sources.list file:

```
gksudo /etc/apt/sources.list
```

and try to change all http to ftp instead (Only on uncommented lines - those without #). Save and close then retry your update.

same problem with the ftp as well.may be some problem with my college firewall.i'll have to talk to my admins:( nyway thanx for the help.:)

---

### Post by zombrax on 2008-06-14
hey bro,

I had the exact same problem and it took me 4 weeks to work out the solution; I typed the wrong Proxy IP address. I checked it a million times and it LOOKED ok; till i wrote it down on paper and it finally dawned on me that 198.168.1.1 is quite different to 192.168.1.1....

it might be just a simple solution as this... apologies if this doesn't help :)

---

