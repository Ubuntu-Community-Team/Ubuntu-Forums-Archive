---
title: "Failure to update"
date: 2021-05-04
forum: General Help
---

### Post by Panawe on 2021-05-04
When prompted to update this morning I got the following error message:

>  This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
 Transaction failed: Package dependencies cannot be resolved
  The following packages have unmet dependencies:
 
 
 grub-efi-amd64-signed: Depends: grub2-common (>= 2.02~beta2-36ubuntu3.31) but 2.04-1ubuntu26.11 is to be installed
  

I realise the problem is the workaround I installed to enable to move easily between Linux and Windows. Can anyone suggest a solution?

TIA

---

### Post by ActionParsnip on 2021-05-04
What is the output of
```

apt-cache policy grub-efi-amd64-signed grub2-common; lsb_release -a; uname -a

```
Thanks

---

### Post by Panawe on 2021-05-04
Thanks for responding. I get the following response from Terminal:

```
grub-efi-amd64-signed:
  Installed: 1.142.11+2.04-1ubuntu26.9
  Candidate: 1.167+2.04-1ubuntu44
  Version table:
     1.167+2.04-1ubuntu44 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages
 *** 1.142.11+2.04-1ubuntu26.9 100
        100 /var/lib/dpkg/status
     1.142.4+2.04-1ubuntu26.2 500
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 Packages
     1.142+2.04-1ubuntu26 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal/main amd64 Packages
grub2-common:
  Installed: 2.04-1ubuntu26.9
  Candidate: 2.04-1ubuntu26.11
  Version table:
     2.04-1ubuntu26.11 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages
 *** 2.04-1ubuntu26.9 100
        100 /var/lib/dpkg/status
     2.04-1ubuntu26.2 500
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 Packages
     2.04-1ubuntu26 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal/main amd64 Packages
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:    20.04
Codename:    focal

Command 'phil' not found, did you mean:

  command 'pil' from deb picolisp (19.12-1)

Try: sudo apt install <deb name>


```

Probably doing something wrong.

TIA

---

### Post by streetfeed on 2021-05-04
When doing an update on 5/4/21 I received the same message. I'm running a generic Dell 9310 factory install of Ubuntu 20.04.2 LTS.

---

### Post by &amp;KyT$0P# on 2021-05-04
Can you please post the output from running these commands in Terminal -
```
sudo apt-get update
apt-get -s dist-upgrade
```

---

### Post by Panawe on 2021-05-05
Okay, here goes:

```
sudo apt-get -s dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  gnome-shell-extension-appindicator grub-common grub-efi-amd64
  grub-efi-amd64-bin grub-efi-amd64-signed grub2-common libldap-2.4-2
  libldap-2.4-2:i386 libldap-common openvpn python3-distupgrade
  ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk update-notifier
  update-notifier-common
15 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Inst ubuntu-release-upgrader-gtk [1:20.04.30] (1:20.04.32 Ubuntu:20.04/focal-updates [all]) []
Inst ubuntu-release-upgrader-core [1:20.04.30] (1:20.04.32 Ubuntu:20.04/focal-updates [all]) []
Inst python3-distupgrade [1:20.04.30] (1:20.04.32 Ubuntu:20.04/focal-updates [all])
Inst update-notifier [3.192.30.5] (3.192.30.7 Ubuntu:20.04/focal-updates [amd64]) []
Inst update-notifier-common [3.192.30.5] (3.192.30.7 Ubuntu:20.04/focal-updates [all])
Inst gnome-shell-extension-appindicator [33.1-0ubuntu0.20.04.1] (33.1-0ubuntu0.20.04.2 Ubuntu:20.04/focal-updates [all])
Inst grub-efi-amd64 [2.04-1ubuntu26.9] (2.04-1ubuntu44 Ubuntu:20.04/focal-updates [amd64]) []
Inst grub2-common [2.04-1ubuntu26.9] (2.04-1ubuntu26.11 Ubuntu:20.04/focal-updates [amd64]) []
Inst grub-efi-amd64-signed [1.142.11+2.04-1ubuntu26.9] (1.167+2.04-1ubuntu44 Ubuntu:20.04/focal-updates [amd64]) []
Inst grub-efi-amd64-bin [2.04-1ubuntu26.9] (2.04-1ubuntu44 Ubuntu:20.04/focal-updates [amd64]) []
Inst grub-common [2.04-1ubuntu26.9] (2.04-1ubuntu26.11 Ubuntu:20.04/focal-updates [amd64])
Inst libldap-common [2.4.49+dfsg-2ubuntu1.7] (2.4.49+dfsg-2ubuntu1.8 Ubuntu:20.04/focal-updates [all])
Inst libldap-2.4-2 [2.4.49+dfsg-2ubuntu1.7] (2.4.49+dfsg-2ubuntu1.8 Ubuntu:20.04/focal-updates [amd64]) [libldap-2.4-2:amd64 on libldap-2.4-2:i386] [libldap-2.4-2:i386 on libldap-2.4-2:amd64] [libldap-2.4-2:i386 ]
Inst libldap-2.4-2:i386 [2.4.49+dfsg-2ubuntu1.7] (2.4.49+dfsg-2ubuntu1.8 Ubuntu:20.04/focal-updates [i386])
Inst openvpn [2.4.7-1ubuntu2] (2.4.7-1ubuntu2.20.04.2 Ubuntu:20.04/focal-updates, Ubuntu:20.04/focal-security [amd64])
Conf ubuntu-release-upgrader-gtk (1:20.04.32 Ubuntu:20.04/focal-updates [all])
Conf ubuntu-release-upgrader-core (1:20.04.32 Ubuntu:20.04/focal-updates [all])
Conf python3-distupgrade (1:20.04.32 Ubuntu:20.04/focal-updates [all])
Conf update-notifier (3.192.30.7 Ubuntu:20.04/focal-updates [amd64])
Conf update-notifier-common (3.192.30.7 Ubuntu:20.04/focal-updates [all])
Conf gnome-shell-extension-appindicator (33.1-0ubuntu0.20.04.2 Ubuntu:20.04/focal-updates [all])
Conf grub-efi-amd64 (2.04-1ubuntu44 Ubuntu:20.04/focal-updates [amd64])
Conf grub2-common (2.04-1ubuntu26.11 Ubuntu:20.04/focal-updates [amd64])
Conf grub-efi-amd64-signed (1.167+2.04-1ubuntu44 Ubuntu:20.04/focal-updates [amd64])
Conf grub-efi-amd64-bin (2.04-1ubuntu44 Ubuntu:20.04/focal-updates [amd64])
Conf grub-common (2.04-1ubuntu26.11 Ubuntu:20.04/focal-updates [amd64])
Conf libldap-common (2.4.49+dfsg-2ubuntu1.8 Ubuntu:20.04/focal-updates [all])
Conf libldap-2.4-2 (2.4.49+dfsg-2ubuntu1.8 Ubuntu:20.04/focal-updates [amd64])
Conf libldap-2.4-2:i386 (2.4.49+dfsg-2ubuntu1.8 Ubuntu:20.04/focal-updates [i386])
Conf openvpn (2.4.7-1ubuntu2.20.04.2 Ubuntu:20.04/focal-updates, Ubuntu:20.04/focal-security [amd64]
```

```
 sudo apt-get update
 [sudo] password for phil:  
 Hit:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal InRelease
 Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates InRelease
 Hit:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease
 Hit:4 [http://ppa.launchpad.net/gencfsm/ppa/ubuntu](http://ppa.launchpad.net/gencfsm/ppa/ubuntu) focal InRelease
 Hit:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-backports InRelease       
 Hit:6 [http://ppa.launchpad.net/stefansundin/truecrypt/ubuntu](http://ppa.launchpad.net/stefansundin/truecrypt/ubuntu) focal InRelease
 Hit:7 [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) focal InRelease
 Hit:8 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) focal InRelease
 Reading package lists... Done
  
```

Hope this helps.

TIA

---

### Post by &amp;KyT$0P# on 2021-05-05
I'm not seeing any problems there.  Does it resolve this if you perform the updates by running
```
sudo apt-get dist-upgrade
```

---

### Post by Panawe on 2021-05-06
Yes, all seems okay now.

Thanks.

---

### Post by John Nagle on 2021-05-08
I got that message, too, from the updater starting itself. I didn't request an update.  "Not all updates can be installed. Run a partial upgrade, to install as many update as possible."
No useful error messages about what it's unhappy about. Lame.
This is on Ubuntu 16.04 LTS, but I got the same message today on a Ubuntu 20.04 LTS system.

I ran Synaptic Package Manager and it reported "0 broken packages". So packages are supposedly in a valid state.


Some system state info, as someone requested above:

 [FONT=courier new]apt-cache policy grub-efi-amd64-signed grub2-common; lsb_release -a; uname -a
grub-efi-amd64-signed:
  Installed: 1.93.24+2.02-2ubuntu8.21
  Candidate: 1.167~18.04.1+2.04-1ubuntu44
  Version table:
     1.167~18.04.1+2.04-1ubuntu44 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages
 *** 1.93.24+2.02-2ubuntu8.21 100
        100 /var/lib/dpkg/status
     1.93.19+2.02-2ubuntu8.17 500
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 Packages
     1.93+2.02-2ubuntu8 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages
grub2-common:
  Installed: 2.02-2ubuntu8.21
  Candidate: 2.02-2ubuntu8.23
  Version table:
     2.02-2ubuntu8.23 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages
 *** 2.02-2ubuntu8.21 100
        100 /var/lib/dpkg/status
     2.02-2ubuntu8.17 500
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 Packages
     2.02-2ubuntu8 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages
LSB Version:    core-9.20170808ubuntu1-noarch:printing-9.20170808ubuntu1-noarch:security-9.20170808ubuntu1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.5 LTS
Release:    18.04
Codename:    bionic


[/FONT]

---

