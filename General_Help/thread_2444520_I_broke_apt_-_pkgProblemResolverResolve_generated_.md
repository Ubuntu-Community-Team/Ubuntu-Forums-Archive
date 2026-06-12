---
title: "I broke apt - pkgProblemResolver::Resolve generated breaks, this may be caused by hel"
date: 2020-05-31
forum: General Help
---

### Post by Dragon777 on 2020-05-31
Hi,   

I tried installing a couple of packages and it seems ive broken apt 

```
ca@ca-ThinkPad-X1-Carbon-6th:~/Downloads$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04 LTS
Release:        20.04
Codename:       focal
ca@ca-ThinkPad-X1-Carbon-6th:~/Downloads$ sudo apt install --fix-broken
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 gcc-10-base : Breaks: gcc-10-base:i386 (!= 10.1.0-3) but 10.1.0-2ubuntu1~18.04 is installed
 gcc-10-base:i386 : Breaks: gcc-10-base (!= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
 lib32gcc-s1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
 lib32gcc1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
 libatomic1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
 libcc1-0 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
 libgcc-s1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
 libgcc1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
 libgomp1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
 libitm1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
 liblsan0 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
 libquadmath0 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
 libstdc++6 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
 libtsan0 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```\

edit: I m trying to install this package 
```
ca@ca-ThinkPad-X1-Carbon-6th:~/Downloads$ sudo apt install -f libgl1-mesa-dri:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 gcc-10-base : Breaks: gcc-10-base:i386 (!= 10.1.0-3) but 10.1.0-2ubuntu1~18.04 is to be installed
 gcc-10-base:i386 : Breaks: gcc-10-base (!= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 lib32gcc-s1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 lib32gcc1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 libatomic1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 libcc1-0 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 libgcc-s1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 libgcc1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 libgl1-mesa-dri : Breaks: libgl1-mesa-dri:i386 (!= 20.1.0~kisak2~e) but 20.0.4-2ubuntu1 is to be installed
 libgl1-mesa-dri:i386 : Depends: libdrm-amdgpu1:i386 (>= 2.4.100) but it is not going to be installed
                        Depends: libdrm-intel1:i386 (>= 2.4.38) but it is not going to be installed
                        Depends: libdrm-nouveau2:i386 (>= 2.4.66) but it is not going to be installed
                        Depends: libdrm-radeon1:i386 (>= 2.4.31) but it is not going to be installed
                        Depends: libdrm2:i386 (>= 2.4.75) but it is not going to be installed
                        Depends: libelf1:i386 (>= 0.142) but it is not going to be installed
                        Depends: libexpat1:i386 (>= 2.0.1) but it is not going to be installed
                        Depends: libglapi-mesa:i386 (= 20.0.4-2ubuntu1) but it is not going to be installed
                        Depends: libllvm9:i386 (>= 1:9~svn298832-1~) but it is not going to be installed
                        Depends: libsensors5:i386 (>= 1:3.5.0) but it is not going to be installed
                        Depends: libstdc++6:i386 (>= 5.2) but it is not going to be installed
                        Depends: libvulkan1:i386 (>= 1.2.131.2) but it is not going to be installed
                        Breaks: libgl1-mesa-dri (!= 20.0.4-2ubuntu1) but 20.1.0~kisak2~e is to be installed
 libgomp1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 libitm1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 liblsan0 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 libquadmath0 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 libstdc++6 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 libtsan0 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

   I am not sure what do to now lol

---

### Post by DuckHook on 2020-05-31
Please provide more than just bare-bones info:

[list=1]
[*]Why are you trying to install a 32-bit system library in Focal??? 32-bit has been deprecated. It will be especially bad in something like mesa.
[*]Even if the above were acceptable, you must first activate 32-bit architecture before you can install 32-bit libs.
[*]Why are you mixing version repos? This is a big no-no. What did you do?
[*]I don't want to be presumptuous, but doing an organ transplant of the sort you are attempting implies guru-level skills whereas mixing version repos and not understanding the need for 32-bit architecture implies the opposite.
[*]Therefore, best tell us what your level of Linux expertise is, detailed steps as to what steps you've taken so far, and especially **what your ultimate end goal is**.
[/list]

---

### Post by Dragon777 on 2020-06-01
I tried installing lutris and it required it  [https://github.com/lutris/docs/blob/master/InstallingDrivers.md](https://github.com/lutris/docs/blob/master/InstallingDrivers.md)

```
**If you have Ubuntu 19.10 or newer:** Enable 32 bit architecture (if you haven't already):
 sudo dpkg --add-architecture i386 
 Update to refresh packages:
 sudo apt update
 Install support for 32-bit games:
 sudo apt install libgl1-mesa-dri:i386

```

I'm still a newbie, i am note sure what ive done wrong but it seems I cannot use apt anymore to install package now. Is it possible to get the system back as before?

Thanks

---

### Post by dino99 on 2020-06-01
unset external source(s) ,update and downgrade package(s) to genuine version (via synaptic)
also clean the system via clean/autoclean/autoremove
then glance at 'journalctl -b' output into a terminal (red line = error; yellow line = warning)

---

### Post by deadflowr on 2020-06-01
Your output currently shows as 20.04,
but the gcc-10-base package *10.1.0-2ubuntu1~18.04* is only available for 18.04 from the toolchain ppa:
[https://launchpad.net/~ubuntu-toolchain-r/+archive/ubuntu/test]("https://launchpad.net/~ubuntu-toolchain-r/+archive/ubuntu/test")
(18.04 has never had gcc-10 in it's repositories)

I have no idea where the *10.1.0-3* package version is from, but to venture a guess it's just about the version of what the 20.10 development release has.
gcc-10 on 20.04 is 10.20200411 for all gcc-10 related packages.
But none of the output shows any of that.


Was this an upgrade?

---

### Post by DuckHook on 2020-06-01
Lots of good advice from dino99 and deadflowr. I don't want to overwhelm you with advice, so:

[list]
[*]Try their suggestions first.
[*]Answer their questions/post back findings.
[/list]
But after your system is put back into shape, please consider the following:

New users often make the mistake (understandable) of trying to change their base system too much. These include adding apps from outside the official repos, using PPAs, etc. This is made worse by the fact that Internet searches are filled with bad advice that will break systems. Therefore, at least for new users:

[list=1]
[*]Keep your base system as close to default as possible.
[*]This means no adding of PPAs or outside apps.
[*]Even official repo apps should be added sparingly.
[*]Instead, install a VM like KVM/QEMU, Virtualbox, VMWare, Xen, etc
[*]Install all of your wild and woolly apps in the VM. You simply roll back to a good snapshot if anything breaks.
[/list]
By simply keeping your base system clean, you will avoid most of the problems that new users run into with Ubuntu.

---

### Post by Dragon777 on 2020-06-02
Thanks for all your help.

> unset external source(s) ,update and downgrade package(s) to genuine version (via synaptic)
also clean the system via clean/autoclean/autoremove
then glance at 'journalctl -b' output into a terminal (red line = error; yellow line = warning)

here is my sources.list
```
ca@ca-ThinkPad-X1-Carbon-6th:~$ sudo cat /etc/apt/sources.list

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://klid.dk/ftp/ubuntu/ focal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://klid.dk/ftp/ubuntu/ focal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://klid.dk/ftp/ubuntu/ focal universe
deb http://klid.dk/ftp/ubuntu/ focal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://klid.dk/ftp/ubuntu/ focal multiverse
deb http://klid.dk/ftp/ubuntu/ focal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://klid.dk/ftp/ubuntu/ focal-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

deb http://klid.dk/ftp/ubuntu/ focal-security main restricted
deb http://klid.dk/ftp/ubuntu/ focal-security universe
deb http://klid.dk/ftp/ubuntu/ focal-security multiverse

```

```
a@ca-ThinkPad-X1-Carbon-6th:~$ sudo apt update                                                       
Hit:1 http://ftp.klid.dk/ftp/ubuntu focal InRelease
Hit:2 http://ftp.klid.dk/ftp/ubuntu focal-updates InRelease
Hit:3 http://ftp.klid.dk/ftp/ubuntu focal-backports InRelease
Hit:4 http://ftp.klid.dk/ftp/ubuntu focal-security InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
5 packages can be upgraded. Run 'apt list --upgradable' to see them.
ca@ca-ThinkPad-X1-Carbon-6th:~$ sudo apt list --upgradable
Listing... Done
ca-certificates/focal-updates,focal-updates,focal-security,focal-security 20190110ubuntu1.1 all [upgradable from: 20190110ubuntu1]
libfreerdp-client2-2/focal-updates,focal-security 2.1.1+dfsg1-0ubuntu0.20.04.1 amd64 [upgradable from: 2.0.0~git20190204.1.2693389a+dfsg1-2build2]
libfreerdp2-2/focal-updates,focal-security 2.1.1+dfsg1-0ubuntu0.20.04.1 amd64 [upgradable from: 2.0.0~git20190204.1.2693389a+dfsg1-2build2]
libwinpr2-2/focal-updates,focal-security 2.1.1+dfsg1-0ubuntu0.20.04.1 amd64 [upgradable from: 2.0.0~git20190204.1.2693389a+dfsg1-2build2]
vinagre/focal-updates,focal-security 3.22.0-7ubuntu0.20.04.1 amd64 [upgradable from: 3.22.0-7]
ca@ca-ThinkPad-X1-Carbon-6th:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 gcc-10-base : Breaks: gcc-10-base:i386 (!= 10.1.0-3) but 10.1.0-2ubuntu1~18.04 is installed
 gcc-10-base:i386 : Breaks: gcc-10-base (!= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
 lib32gcc-s1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
 lib32gcc1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
 libatomic1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
 libcc1-0 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
 libgcc-s1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
 libgcc1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
 libgomp1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
 libitm1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
 liblsan0 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
 libquadmath0 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
 libstdc++6 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
 libtsan0 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

I cant install synaptic either as it seems I cant use apt anymore
```
ca@ca-ThinkPad-X1-Carbon-6th:~$ sudo apt install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 gcc-10-base : Breaks: gcc-10-base:i386 (!= 10.1.0-3) but 10.1.0-2ubuntu1~18.04 is to be installed
 gcc-10-base:i386 : Breaks: gcc-10-base (!= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 lib32gcc-s1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 lib32gcc1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 libatomic1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 libcc1-0 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 libgcc-s1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 libgcc1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 libgomp1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 libitm1 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 liblsan0 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 libquadmath0 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 libstdc++6 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 libtsan0 : Depends: gcc-10-base (= 10.1.0-2ubuntu1~18.04) but 10.1.0-3 is to be installed
 synaptic : Depends: libept1.6.0 but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

> Your output currently shows as 20.04,
but the gcc-10-base package *10.1.0-2ubuntu1~18.04* is only available for 18.04 from the toolchain ppa:
[https://launchpad.net/~ubuntu-toolch...ve/ubuntu/test]("https://launchpad.net/~ubuntu-toolchain-r/+archive/ubuntu/test")
(18.04 has never had gcc-10 in it's repositories)

I have no idea where the *10.1.0-3* package version is from, but to venture a guess it's just about the version of what the 20.10 development release has.
gcc-10 on 20.04 is 10.20200411 for all gcc-10 related packages.
But none of the output shows any of that.


Was this an upgrade? 		

yes I tried upgrading from 18 to 19 and then 19 to 20

---

