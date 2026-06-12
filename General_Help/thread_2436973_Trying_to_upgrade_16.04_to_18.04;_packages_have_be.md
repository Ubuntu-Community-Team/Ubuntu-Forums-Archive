---
title: "Trying to upgrade 16.04 to 18.04; packages have been kept back: libgdiplus"
date: 2020-02-16
forum: General Help
---

### Post by maxburn on 2020-02-16
Edit; assuming I did some things wrong below I've restored the VM to before I started this mess and my apps are functioning again but I still would like to know how to resolve this and get it up to 18.04. 

Trying to upgrade a personal automation server, it does have some mono apps on it.

do-release-upgrade results in: Please install all available updates for your release before upgrading.

```
user@computer:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-166 linux-headers-4.4.0-166-generic linux-image-4.4.0-166-generic linux-modules-4.4.0-166-generic linux-modules-extra-4.4.0-166-generic
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  libgdiplus
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
user@computer:~$ sudo apt-get install libgdiplus
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgdiplus : Depends: libgif4 (>= 4.1.4) but it is not installable
              Depends: libjpeg62-turbo (>= 1.3.1) but it is not installable
E: Unable to correct problems, you have held broken packages.
user@computer:~$
```

```
$ sudo aptitude
sudo: aptitude: command not found
```

So I uninstalled libgdiplus and tried to reinstall; 

```
$ sudo apt install libgdiplus
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgdiplus : Depends: libgif4 (>= 4.1.4) but it is not installable
              Depends: libjpeg62-turbo (>= 1.3.1) but it is not installable
E: Unable to correct problems, you have held broken packages.
```

Saw some advice on wget and manually installing these. Went out and found libjpeg62-turbo, installed it and it didn't reduce my errors; 

```
giflib-5.2.1.tar  giflib-5.2.1.tar.gz  libjpeg-turbo-official_2.0.4_amd64.deb
user@computer:~/install$ sudo dpkg --install --recursive --auto-deconfigure libjpeg-turbo-official_2.0.4_amd64.deb
Selecting previously unselected package libjpeg-turbo-official.
(Reading database ... 139257 files and directories currently installed.)
Preparing to unpack libjpeg-turbo-official_2.0.4_amd64.deb ...
Unpacking libjpeg-turbo-official (2.0.4-20191231) ...
Setting up libjpeg-turbo-official (2.0.4-20191231) ...
user@computer:~/install$ sudo apt-get install libgdiplus
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgdiplus : Depends: libgif4 (>= 4.1.4) but it is not installable
              Depends: libjpeg62-turbo (>= 1.3.1) but it is not installable
E: Unable to correct problems, you have held broken packages.
user@computer:~/install$
```

What do I do now?

---

### Post by maxburn on 2020-02-16
Also; 

```
user@computer:~/install$ sudo apt-get install mono-devel
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 mono-devel : Depends: libmono-system-design4.0-cil (>= 1.0) but it is not going to be installed
              Depends: libmono-system-drawing-design4.0-cil (>= 1.0) but it is not going to be installed
              Depends: libmono-system-drawing4.0-cil (>= 3.0.6) but it is not going to be installed
              Depends: libmono-system-messaging4.0-cil (>= 2.10.1) but it is not going to be installed
              Depends: libmono-system-runtime4.0-cil (>= 2.10.1) but it is not going to be installed
              Depends: libmono-system-servicemodel-activation4.0-cil (>= 1.0) but it is not going to be installed
              Depends: libmono-system-servicemodel-web4.0-cil (>= 3.2.1) but it is not going to be installed
              Depends: libmono-system-servicemodel4.0a-cil (>= 3.2.3) but it is not going to be installed
              Depends: libmono-system-web-extensions4.0-cil (>= 2.10.3) but it is not going to be installed
              Depends: libmono-system-web-services4.0-cil (>= 1.0) but it is not going to be installed
              Depends: libmono-system-web-webpages-razor2.0-cil (>= 1.0) but it is not going to be installed
              Depends: libmono-system-web-webpages2.0-cil (>= 1.0) but it is not going to be installed
              Depends: libmono-system-web4.0-cil (>= 2.10.3) but it is not going to be installed
              Depends: libmono-system-windows-forms4.0-cil (>= 1.0) but it is not going to be installed
              Depends: libmono-cil-dev (= 5.18.1.0-0xamarin4+debian8b1) but it is not going to be installed
              Recommends: msbuild but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Not sure how all this got broken.

---

### Post by Impavidus on 2020-02-17
Your libgdiplus depends on libgif4 and libjpeg62-turbo. The libgdiplus from the official repositories depends on libgif7 and libjpeg8, which appear to be newer. There is no libgif4 or libjpeg62-turbo in the official repositories of Ubuntu 16.04. Which make me wonder where your libgdiplus comes from. Something in your repositories must be messed up. Can you show us the output of:```
sudo apt-get update
apt-cache policy libgdiplus
```

---

