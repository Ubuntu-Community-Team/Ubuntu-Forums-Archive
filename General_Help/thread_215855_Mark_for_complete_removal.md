---
title: "Mark for complete removal"
date: 2006-07-14
forum: General Help
---

### Post by nami on 2006-07-14
Hi

I removed a package from synaptics using the "mark for complete removal".  Now I want it back and it will not show up even if I do a search.

How do I get it back?

Thanks

nami

---

### Post by Athropos on 2006-07-14
This only removes the installed version, you should still be able to re-install it. If you can't find it anymore in Synaptic, it was either a local package or it has been removed from the repos.

---

### Post by nami on 2006-07-14
The package I "mark for complete removal" was vmware player ???

---

### Post by aysiu on 2006-07-14
Can you post the output of these three commands? ```
sudo aptitude update
sudo aptitude install vmware-player
cat /etc/apt/sources.list
```

---

### Post by nami on 2006-07-14
yup

> nami@nami-desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release [30.9kB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Bad header line [IP: 82.211.81.182 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release [19.6kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources [24.9kB]
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages [866B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages [14B]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages [14B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages [14B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
  Got a single header line over 360 chars [IP: 82.211.81.182 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
  Bad header line [IP: 82.211.81.182 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
  0 OK [IP: 82.211.81.182 80]
Fetched 76.3kB in 1s (70.4kB/s)
Reading package lists... Done
nami@nami-desktop:~$ sudo aptitude install vmware-player
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No candidate version found for vmware-player
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
nami@nami-desktop:~$ cat /etc/apt/sources.list

deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531.2)]/ dapper main restricted
nami@nami-desktop:~$

---

### Post by aysiu on 2006-07-14
Something looks weird with your sources.list.

Can you try getting a fresh list?
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

And then trying again? ```
sudo aptitude update
sudo aptitude install vmware-player
```

---

### Post by nami on 2006-07-14
I tired that but am still getting errors with the first command:

> nami@nami-desktop:~$ [COLOR="DeepSkyBlue"]sudo aptitude update[/COLOR]
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
[COLOR="Red"]Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
  Connection failed[/COLOR]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
[COLOR="Red"]Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
  Connection failed
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
  Connection failed
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
  Connection failed
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
  Connection failed[/COLOR]
Fetched 569B in 1s (411B/s)
Reading package lists... Done
nami@nami-desktop:~$


> nami@nami-desktop:~$ [COLOR="DeepSkyBlue"]sudo aptitude install vmware-player[/COLOR]
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
[COLOR="Red"]No candidate version found for vmware-player
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/COLOR]
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
nami@nami-desktop:~$


---

### Post by aysiu on 2006-07-14
That's weird, especially since the ones that had failed connections aren't even the ones that have *vmware-player* in them.

---

### Post by nami on 2006-07-14
Hmmmmmm, interesting! :-k

---

### Post by nami on 2006-07-14
Does this mean I have to do another re-install.  I've already done that 4 times this week!

---

### Post by HAARP on 2006-07-14
Download VMware player at their site:
[http://download3.vmware.com/software/vmplayer/VMware-player-1.0.1-19317.i386.rpm](http://download3.vmware.com/software/vmplayer/VMware-player-1.0.1-19317.i386.rpm)
It's a rpm-archive.

Get "alien" from the repos. In terminal, type:
```
alien -k --scripts VMware-player-1.0.1-19317.i386.rpm
```
Wait for it to finish. Ta-dah, you've got a deb-archive you can install by double-cklicking on it :)

---

### Post by nami on 2006-07-14
I read your post too late HAARP.

Anyway, I did a fresh install and tried the steps again:

> nami@nami-desktop:~$ [COLOR="DeepSkyBlue"]sudo aptitude update[/COLOR]
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Fetched 5B in 1s (4B/s)
Reading package lists... Done
nami@nami-desktop:~$ [COLOR="DeepSkyBlue"]sudo aptitude install vmware-player[/COLOR]
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  libssl0.9.7 vmware-player-kernel-modules
  vmware-player-kernel-modules-2.6.15-23
The following NEW packages will be installed:
  libssl0.9.7 vmware-player vmware-player-kernel-modules
  vmware-player-kernel-modules-2.6.15-23
0 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.2MB of archives. After unpacking 37.7MB will be used.
Do you want to continue? [Y/n/?]
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse vmware-player-kernel-modules-2.6.15-23 2.6.15.10-6 [165kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse vmware-player-kernel-modules 2.6.15.10-6 [6762B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libssl0.9.7 0.9.7g-5ubuntu1 [2176kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse vmware-player 1.0.1-4 [11.8MB]Fetched 14.2MB in 30s (465kB/s)
Preconfiguring packages ...
Selecting previously deselected package vmware-player-kernel-modules-2.6.15-23.
(Reading database ... 105439 files and directories currently installed.)
Unpacking vmware-player-kernel-modules-2.6.15-23 (from .../vmware-player-kernel-modules-2.6.15-23_2.6.15.10-6_i386.deb) ...
Selecting previously deselected package vmware-player-kernel-modules.
Unpacking vmware-player-kernel-modules (from .../vmware-player-kernel-modules_2.6.15.10-6_all.deb) ...
Selecting previously deselected package libssl0.9.7.
Unpacking libssl0.9.7 (from .../libssl0.9.7_0.9.7g-5ubuntu1_i386.deb) ...
Selecting previously deselected package vmware-player.
Unpacking vmware-player (from .../vmware-player_1.0.1-4_i386.deb) ...
Setting up vmware-player-kernel-modules-2.6.15-23 (2.6.15.10-6) ...

Setting up vmware-player-kernel-modules (2.6.15.10-6) ...
Setting up libssl0.9.7 (0.9.7g-5ubuntu1) ...

Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.237.0/255.255.255.0 appears to be unused.

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.88.0/255.255.255.0 appears to be unused.

Starting VMware services:
   Virtual machine monitor                                            [COLOR="Red"]failed[/COLOR]
   Virtual ethernet                                                   [COLOR="Red"]failed[/COLOR]
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" [COLOR="Red"]failed[/COLOR].
[COLOR="Red"]dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
A package failed to install.  Trying to recover:
Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.129.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install
already exists.  Overwrite? [yes]

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.70.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes]

Starting VMware services:
   Virtual machine monitor                                            [COLOR="Red"]failed[/COLOR]
   Virtual ethernet                                                   [COLOR="Red"]failed[/COLOR]
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

[COLOR="Red"]invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player[/COLOR]
nami@nami-desktop:~$


Why did it fail?

---

### Post by leo_m on 2006-07-14
Why bother with this vmware-player?  Instead, get vmware-server, download that from vmware web-site, then build that (you *may* have to download a few packages required to build that): it will compile a fresh vmnet module for you, the one where you are getting errors in vmware-player.  Note that, however, every time you upgrade your kernel, you will likely have to build the vmware-server again (actually, quite easy and not much time consuming either, just running the perl script which comes with vmware server download)

---

### Post by nami on 2006-07-14
I've tried vmware server but each time i try to install it, it says i already have another version of vmware installed even when i have removed vmware player ???

---

