---
title: "how to fix a broken package"
date: 2012-10-22
forum: General Help
---

### Post by StevenHodges92 on 2012-10-22
I cant install wine because my wine1.5 and wine1.4 packages are both broken somehow.  How do I fix this?

---

### Post by Polydorus on 2012-10-22
I believe the Software Center (?) will fix them for you.  I'm using Synaptic which also repairs packages.

---

### Post by StevenHodges92 on 2012-10-22
when i go to edit - fix broken packages, then hit apply, I get this:

Could not apply changes!
Fix broken packages first.

---

### Post by Polydorus on 2012-10-22
I'm now in my fifth week of using Linux of any sort so all this is new to me.  It would help answer your question if you posted what distro you are using and what you mean by "when i go to edit - fix broken packages" i.e. where that message comes from.

---

### Post by raja.genupula on 2012-10-22
you can actually fix the broken packages by the command 
```
sudo apt-get install -f 
```

you have to do that in terminal .

---

### Post by StevenHodges92 on 2012-10-22
When I do that, this comes up

> steven@ubuntu:~$ sudo apt-get install -f
[sudo] password for steven: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
steven@ubuntu:~$ 

All I have open is the terminal, synaptic package manager, software center, and mozilla firefox

---

### Post by raja.genupula on 2012-10-22
yes , actually that because you have stopped the apt-get action in middle without completing 100% . so there it is . 

to make it clear you have to run this 

sudo rm -rf /var/lib/dpkg/lock

---

### Post by StevenHodges92 on 2012-10-22
Now in the synaptic package manager, when I try to fix broken packages I get this

: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies


and when I do
sudo apt-get install -f
I get

steven@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcapi20-3 libgif4 libmpg123-0 libodbc1 libopenal-data libopenal1
  libosmesa6 libtiff4 odbcinst odbcinst1debian2 unixodbc
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
steven@ubuntu:~$ 


But I can still not install the wine packages.

---

### Post by StevenHodges92 on 2012-10-22
I even did this

```
sudo aptitude [Enter or Return key]
[type your password] [Enter or Return key]

Aptitude will start, and after it stops churning ...

Under the View menu, select Audit Recommendations. Wait. Accept the audit recommendations, and that should fix it.

Ubuntu is well worth enduring a little trouble like this! Don't give up!
```

from another post and I did it for the 2 things listed until it said no packages to be done anything to, and I still cant fix broken packages or install wine.

---

### Post by dino99 on 2012-10-22
possible workaround:

- if you have some app(s) already installed into a previous .wine folder and dont want to loose it(them), then simply rename that .wine folder to what you want, for example .wine_old . Otherwise, delete that .wine folder.

- then your installation issue might be due to packages conflict. So post here  the result of:  cat /etc/apt/sources.list

note that wine is still a 32 bits soft, but can be installed on 64 bits. [http://askubuntu.com/questions/74690/how-to-install-32-bit-wine-on-64-bit-ubuntu](http://askubuntu.com/questions/74690/how-to-install-32-bit-wine-on-64-bit-ubuntu)

- and dont forget to clean the room first:
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

---

### Post by StevenHodges92 on 2012-10-22
This is what I get from a fresh new terminal

steven@ubuntu:~$ sudo apt-get clean
[sudo] password for steven: 
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
steven@ubuntu:~$ sudo apt-get autoclean
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
steven@ubuntu:~$ sudo apt-get autoremove
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
steven@ubuntu:~$ cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates main restricted universe multiverse
steven@ubuntu:~$ 


And, I'm really new to Linux, but I dont think I had wine installed at all or even a broken wine, but where would it be because I found no folders named wine



EDIT

Restarted and got this

steven@ubuntu:~$ sudo apt-get clean
[sudo] password for steven: 
steven@ubuntu:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
steven@ubuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
steven@ubuntu:~$ cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates main restricted universe multiverse
steven@ubuntu:~$

---

### Post by StevenHodges92 on 2012-10-22
I still need help with this, are my sources bad?

---

### Post by ~LoKe on 2012-10-23
Type this:
```
gksu gedit /etc/apt/sources.list
```
Erase everything inside, then paste this into it:
> #deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release i386]/ Quantal main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse

## Medibuntu - Ubuntu 12.04 "Quantal Quetzal"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) quantal free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) quantal free non-free

# Google software repository
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
Save and exit.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by StevenHodges92 on 2012-10-23
When I do the first line it gives me this at the end

```
Fetched 17.8 MB in 32s (549 kB/s)                                              
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://packages.medibuntu.org quantal InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch http://dl.google.com/linux/deb/dists/stable/non-free/binary-amd64/Packages  404  Not Found [IP: 74.125.137.136 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

And I still can't install wine

---

