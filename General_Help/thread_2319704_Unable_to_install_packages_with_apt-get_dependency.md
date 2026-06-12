---
title: "Unable to install packages with apt-get: dependency problems"
date: 2016-04-06
forum: General Help
---

### Post by ButterflyKandi on 2016-04-06
Hi,
I'm trying to install monit on my 12.04 server, but I get the following error:

```
kandi@turnip:~$ **sudo apt-get -f install monit**
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-generic-lts-trusty : Depends: linux-headers-3.13.0-77-generic but it is not going to be installed
 linux-image-generic-lts-trusty : Depends: linux-image-3.13.0-77-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Hmm... So that didn't work.  I tried apt-get -f install like the message sugested, and I got a different error message now.

```
kandi@turnip:~$ **sudo apt-get -f install**
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-generic-lts-trusty linux-image-generic-lts-trusty
The following packages will be upgraded:
  linux-headers-generic-lts-trusty linux-image-generic-lts-trusty
2 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
3 not fully installed or removed.
Need to get 0 B/4,640 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? **Y**
dpkg: dependency problems prevent configuration of linux-image-generic-lts-trusty:
 linux-image-generic-lts-trusty depends on linux-image-3.13.0-77-generic; however:
  Package linux-image-3.13.0-77-generic is not installed.
dpkg: error processing linux-image-generic-lts-trusty (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of linux-headers-generic-lts-trusty:
 linux-headers-generic-lts-trusty depends on linux-headers-3.13.0-77-generic; however:
  Package linux-headers-3.13.0-77-generic is not installed.
dpkg: error processing linux-headers-generic-lts-trusty (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic-lts-trusty:
 linux-generic-lts-trusty depends on linux-image-generic-lts-trusty; however:
  Package linux-image-generic-lts-trusty is not configured yet.
 linux-generic-lts-trusty depends on linux-headers-generic-lts-trusty; however:
  Package linux-headers-generic-lts-trusty is not configured yet.
dpkg: error processing linux-generic-lts-trusty (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-generic-lts-trusty
 linux-headers-generic-lts-trusty
 linux-generic-lts-trusty
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Well, that didn't work either and I'm not sure what to do next.  If you have any ideas, please let me know.

Thanx, -Kandi :D

---

### Post by Bucky Ball on 2016-04-06
Welcome. Why do you have Trusty issues when you're running Precise? Some creative PPA or kernel additions? There's a start. 

Please do:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
```

... and post the errors, thanks.

---

### Post by ButterflyKandi on 2016-04-06
I'm not sure what is going on with the trusty errors.  I think that perhaps a dist-upgrade failed.  I'm not sure. :confused:  It has been a while since I tried to use this machine, but everything else seems to work OK with it.

Here is what happens when I try those commands.  

```
kandi@turnip:~$ **sudo apt-get autoremove**
[sudo] password for kandi:
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-generic-lts-trusty : Depends: linux-headers-3.13.0-77-generic but it is not installed
 linux-image-generic-lts-trusty : Depends: linux-image-3.13.0-77-generic but it is not installed
E: Unmet dependencies. Try using -f.
```

```
kandi@turnip:~$ **sudo apt-get update**
Hit http://download.webmin.com sarge Release.gpg
Hit http://download.webmin.com sarge Release
Hit http://webmin.mirror.somersettechsolutions.co.uk sarge Release.gpg
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://archive.ubuntu.com precise Release.gpg
Hit http://download.webmin.com sarge/contrib i386 Packages
Hit http://webmin.mirror.somersettechsolutions.co.uk sarge Release
Hit http://ppa.launchpad.net precise Release
Get:1 http://archive.ubuntu.com precise-updates Release.gpg [198 B]
Ign http://download.webmin.com sarge/contrib TranslationIndex
Hit http://webmin.mirror.somersettechsolutions.co.uk sarge/contrib i386 Packages
Hit http://ppa.launchpad.net precise/main Sources
Hit http://archive.ubuntu.com precise-backports Release.gpg
Ign http://webmin.mirror.somersettechsolutions.co.uk sarge/contrib TranslationIndex
Hit http://ppa.launchpad.net precise/main i386 Packages
Hit http://archive.ubuntu.com precise Release
Hit http://ppa.launchpad.net precise/main TranslationIndex
Get:2 http://archive.ubuntu.com precise-updates Release [55.4 kB]
Hit http://ppa.launchpad.net precise/main Translation-en
Hit http://archive.ubuntu.com precise-backports Release
Ign http://download.webmin.com sarge/contrib Translation-en_US
Hit http://archive.ubuntu.com precise/main Sources
Ign http://download.webmin.com sarge/contrib Translation-en
Hit http://archive.ubuntu.com precise/restricted Sources
Hit http://archive.ubuntu.com precise/universe Sources
Ign http://webmin.mirror.somersettechsolutions.co.uk sarge/contrib Translation-en_US
Hit http://archive.ubuntu.com precise/multiverse Sources
Ign http://webmin.mirror.somersettechsolutions.co.uk sarge/contrib Translation-en
Hit http://archive.ubuntu.com precise/main i386 Packages
Hit http://archive.ubuntu.com precise/restricted i386 Packages
Hit http://archive.ubuntu.com precise/universe i386 Packages
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]
Hit http://archive.ubuntu.com precise/multiverse i386 Packages
Hit http://archive.ubuntu.com precise/main TranslationIndex
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise/restricted TranslationIndex
Hit http://archive.ubuntu.com precise/universe TranslationIndex
Get:4 http://archive.ubuntu.com precise-updates/main Sources [496 kB]
Get:5 http://security.ubuntu.com precise-security Release [55.5 kB]
Get:6 http://archive.ubuntu.com precise-updates/restricted Sources [8,708 B]
Get:7 http://archive.ubuntu.com precise-updates/universe Sources [124 kB]
Get:8 http://archive.ubuntu.com precise-updates/multiverse Sources [10.2 kB]
Get:9 http://archive.ubuntu.com precise-updates/main i386 Packages [1,045 kB]
Get:10 http://security.ubuntu.com precise-security/main Sources [141 kB]
Get:11 http://archive.ubuntu.com precise-updates/restricted i386 Packages [16.1 kB]
Get:12 http://archive.ubuntu.com precise-updates/universe i386 Packages [282 kB]
Get:13 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [17.1 kB]
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://archive.ubuntu.com precise-backports/main Sources
Hit http://archive.ubuntu.com precise-backports/restricted Sources
Hit http://archive.ubuntu.com precise-backports/universe Sources
Hit http://archive.ubuntu.com precise-backports/multiverse Sources
Hit http://archive.ubuntu.com precise-backports/main i386 Packages
Hit http://archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://archive.ubuntu.com precise/main Translation-en
Hit http://archive.ubuntu.com precise/multiverse Translation-en
Hit http://archive.ubuntu.com precise/restricted Translation-en
Hit http://archive.ubuntu.com precise/universe Translation-en
Hit http://archive.ubuntu.com precise-updates/main Translation-en
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://archive.ubuntu.com precise-updates/universe Translation-en
Hit http://archive.ubuntu.com precise-backports/main Translation-en
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://archive.ubuntu.com precise-backports/universe Translation-en
Get:14 http://security.ubuntu.com precise-security/restricted Sources [4,476 B]
Get:15 http://security.ubuntu.com precise-security/universe Sources [45.7 kB]
Get:16 http://security.ubuntu.com precise-security/multiverse Sources [2,708 B]
Get:17 http://security.ubuntu.com precise-security/main i386 Packages [657 kB]
Get:18 http://security.ubuntu.com precise-security/restricted i386 Packages [11.6 kB]
Get:19 http://security.ubuntu.com precise-security/universe i386 Packages [137 kB]
Get:20 http://security.ubuntu.com precise-security/multiverse i386 Packages [3,335 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Fetched 3,114 kB in 14s (209 kB/s)
Reading package lists... Done
```

```
kandi@turnip:~$ **sudo apt-get dist-upgrade**
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-generic-lts-trusty : Depends: linux-headers-3.13.0-77-generic but it is not installed
 linux-image-generic-lts-trusty : Depends: linux-image-3.13.0-77-generic but it is not installed
E: Unmet dependencies. Try using -f.
```


Thanks for helping me! -Kandi

---

### Post by ButterflyKandi on 2016-04-06
Hi, just an update, I tried the -f option with autoremove, and I got a little bit different response.

```
kandi@turnip:~$ **sudo apt-get autoremove -f**
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-generic-lts-trusty linux-image-generic-lts-trusty
The following packages will be upgraded:
  linux-headers-generic-lts-trusty linux-image-generic-lts-trusty
2 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
3 not fully installed or removed.
Need to get 0 B/4,640 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? **Y**
dpkg: dependency problems prevent configuration of linux-image-generic-lts-trusty:
 linux-image-generic-lts-trusty depends on linux-image-3.13.0-77-generic; however:
  Package linux-image-3.13.0-77-generic is not installed.
dpkg: error processing linux-image-generic-lts-trusty (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic-lts-trusty:
 linux-headers-generic-lts-trusty depends on linux-headers-3.13.0-77-generic; however:
  Package linux-headers-3.13.0-77-generic is not installed.
dpkg: error processing linux-headers-generic-lts-trusty (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-trusty:
 linux-generic-lts-trusty depends on linux-image-generic-lts-trusty; however:
  Package linux-image-generic-lts-trusty is not configured yet.
 linux-generic-lts-trusty depends on linux-headers-generic-lts-trusty; however:
  Package linux-headers-genNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                     No apport report written because the error message indicates its a followup error from a previous failure.
  No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                            eric-lts-trusty is not configured yet.
dpkg: error processing linux-generic-lts-trusty (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-generic-lts-trusty
 linux-headers-generic-lts-trusty
 linux-generic-lts-trusty
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I'm not sure what went wrong here.  Hopeuflly someone smarter than me can chime in.
Thanx, -Kandi :P

---

### Post by Bucky Ball on 2016-04-06
Could you open a terminal and give us a look at this file please:

> nano /etc/apt/sources.list

---

### Post by ButterflyKandi on 2016-04-06
Sure, no problem.  Hopefully this will tell you want is wrong :(

```
#

# deb cdrom:[Ubuntu-Server 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130214)]/ precise main restricted

# deb cdrom:[Ubuntu-Server 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130214)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ precise universe
deb-src http://archive.ubuntu.com/ubuntu/ precise universe
deb http://archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://archive.ubuntu.com/ubuntu/ precise multiverse
deb http://archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main
```

Thank you! -Kandi :P

---

### Post by Bucky Ball on 2016-04-06
Could be off the money, but [try this]("http://ubuntuforums.org/showthread.php?t=2266430&p=13242029&viewfull=1#post13242029"). Reboot the machine when done and try to update again.

---

### Post by Impavidus on 2016-04-06
Seems to me that you installed 12.04.2, 3 or 4. When support for the kernels coming with those ended in July 2014, you were prompted to upgrade to the trusty kernel. Nothing strange there.

Also, this is no error from the pre-installation script. apt-get doesn't even attempt to install the packages linux-headers-3.13.0-77-generic and linux-image-3.13.0-77-generic. This seems a different problem. apt-get install -f should install these missing packages. Maybe we can ask it to do so explicitly.```
sudo apt-get install -f linux-headers-3.13.0-77-generic linux-image-3.13.0-77-generic
```That should either fix the dependency problem or give a more meaningful error message.

---

### Post by ButterflyKandi on 2016-04-06
> **Bucky Ball said:**
> Could be off the money, but [try this]("http://ubuntuforums.org/showthread.php?t=2266430&p=13242029&viewfull=1#post13242029"). Reboot the machine when done and try to update again.

OK, so I did try changing that setting to force PAE.  I then did an apt-get update and apt-get upgrade and got the same result as last time I think.

```
kandi@turnip:~$ **sudo apt-get upgrade**
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-generic-lts-trusty : Depends: linux-headers-3.13.0-77-generic but it is not installed
 linux-image-generic-lts-trusty : Depends: linux-image-3.13.0-77-generic but it is not installed
E: Unmet dependencies. Try using -f.
kandi@turnip:~$ **sudo apt-get -f install**
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-generic-lts-trusty linux-image-generic-lts-trusty
The following packages will be upgraded:
  linux-headers-generic-lts-trusty linux-image-generic-lts-trusty
2 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
Need to get 0 B/4,640 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of linux-image-generic-lts-trusty:
 linux-image-generic-lts-trusty depends on linux-image-3.13.0-77-generic; however:
  Package linux-image-3.13.0-77-generic is not installed.
dpkg: error processing linux-image-generic-lts-trusty (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of linux-headers-generic-lts-trusty:
 linux-headers-generic-lts-trusty depends on linux-headers-3.13.0-77-generic; however:
  Package linux-headers-3.13.0-77-generic is not installed.
dpkg: error processing linux-headers-generic-lts-trusty (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic-lts-trusty:
 linux-generic-lts-trusty depends on linux-image-generic-lts-trusty; however:
  Package linux-image-generic-lts-trusty is not configured yet.
 linux-generic-lts-trusty depends on linux-headers-generic-lts-trusty; however:
  Package linux-headers-generic-lts-trusty is not configured yet.
dpkg: error processing linux-generic-lts-trusty (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-generic-lts-trusty
 linux-headers-generic-lts-trusty
 linux-generic-lts-trusty
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Hmm... So, I tried to implicitly tell the packages to install as Impavidus suggested.

```
kandi@turnip:~$ **sudo apt-get install -f linux-headers-3.13.0-77-generic linux-image-3.13.0-77-generic**
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-3.13.0-77-generic : Depends: linux-headers-3.13.0-77 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

That complained about a different package (linux-headers-3.13.0-77) being required, so I tried adding that to be implicitly installed as well.


```
kandi@turnip:~$ **sudo apt-get install -f linux-headers-3.13.0-77-generic linux-image-3.13.0-77-generic linux-headers-3.13.0-77**
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  fdutils linux-lts-trusty-doc-3.13.0 linux-lts-trusty-source-3.13.0 linux-lts-trusty-tools
The following NEW packages will be installed:
  linux-headers-3.13.0-77 linux-headers-3.13.0-77-generic linux-image-3.13.0-77-generic
0 upgraded, 3 newly installed, 0 to remove and 3 not upgraded.
3 not fully installed or removed.
Need to get 66.5 MB of archives.
After this operation, 225 MB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-3.13.0-77-generic i386 3.13.0-77.121~precise1 [52.5 MB]
Get:2 http://archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.13.0-77 all 3.13.0-77.121~precise1 [12.8 MB]
Get:3 http://archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.13.0-77-generic i386 3.13.0-77.121~precise1 [1,106 kB]
Fetched 66.5 MB in 42s (1,557 kB/s)
(Reading database ... 917115 files and directories currently installed.)
Unpacking linux-image-3.13.0-77-generic (from .../linux-image-3.13.0-77-generic_3.13.0-77.121~precise1_i386.deb) ...
Done.
Unpacking linux-headers-3.13.0-77 (from .../linux-headers-3.13.0-77_3.13.0-77.121~precise1_all.deb) ...
Unpacking linux-headers-3.13.0-77-generic (from .../linux-headers-3.13.0-77-generic_3.13.0-77.121~precise1_i386.deb) ...
Setting up linux-image-3.13.0-77-generic (3.13.0-77.121~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-77-generic /boot/vmlinuz-3.13.0-77-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-77-generic /boot/vmlinuz-3.13.0-77-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-77-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-77-generic /boot/vmlinuz-3.13.0-77-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-77-generic /boot/vmlinuz-3.13.0-77-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.13.0-85-generic
Found initrd image: /boot/initrd.img-3.13.0-85-generic
Found linux image: /boot/vmlinuz-3.13.0-77-generic
Found initrd image: /boot/initrd.img-3.13.0-77-generic
Found linux image: /boot/vmlinuz-3.13.0-76-generic
Found initrd image: /boot/initrd.img-3.13.0-76-generic
Found linux image: /boot/vmlinuz-3.13.0-74-generic
Found initrd image: /boot/initrd.img-3.13.0-74-generic
Found linux image: /boot/vmlinuz-3.13.0-73-generic
Found initrd image: /boot/initrd.img-3.13.0-73-generic
Found linux image: /boot/vmlinuz-3.13.0-71-generic
Found initrd image: /boot/initrd.img-3.13.0-71-generic
Found linux image: /boot/vmlinuz-3.13.0-68-generic
Found initrd image: /boot/initrd.img-3.13.0-68-generic
Found linux image: /boot/vmlinuz-3.13.0-67-generic
Found initrd image: /boot/initrd.img-3.13.0-67-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-51-generic
Found initrd image: /boot/initrd.img-3.13.0-51-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-generic-lts-trusty (3.13.0.77.69) ...
Setting up linux-headers-3.13.0-77 (3.13.0-77.121~precise1) ...
Setting up linux-headers-3.13.0-77-generic (3.13.0-77.121~precise1) ...
Setting up linux-headers-generic-lts-trusty (3.13.0.77.69) ...
Setting up linux-generic-lts-trusty (3.13.0.77.69) ...
```

So, that seems to do a lot more, and no errors this time.  Very encouraging! So I thought that I would give apt-get upgrade a try.

```
kandi@turnip:~$ **sudo apt-get upgrade**
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  linux-generic-lts-trusty linux-headers-generic-lts-trusty linux-image-generic-lts-trusty
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/6,384 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? **Y**
(Reading database ... 947039 files and directories currently installed.)
Preparing to replace linux-image-generic-lts-trusty 3.13.0.77.69 (using .../linux-image-generic-lts-trusty_3.13.0.85.77_i386.deb) ...
Unpacking replacement linux-image-generic-lts-trusty ...
Preparing to replace linux-headers-generic-lts-trusty 3.13.0.77.69 (using .../linux-headers-generic-lts-trusty_3.13.0.85.77_i386.deb) ...
Unpacking replacement linux-headers-generic-lts-trusty ...
Preparing to replace linux-generic-lts-trusty 3.13.0.77.69 (using .../linux-generic-lts-trusty_3.13.0.85.77_i386.deb) ...
Unpacking replacement linux-generic-lts-trusty ...
Setting up linux-image-generic-lts-trusty (3.13.0.85.77) ...
Setting up linux-headers-generic-lts-trusty (3.13.0.85.77) ...
Setting up linux-generic-lts-trusty (3.13.0.85.77) ...
```

Wow, so this is amazing, no errors for this either! :P

I was able to sucessfully install monit, and no errors at all!  Thank you so much for all your help, you guys are the best!
-Kandi :wink:

---

### Post by Bucky Ball on 2016-04-06
Excellent news. Please mark the thread solved to help future travelers (see first link in my signature below for how).

PS: You needed to reboot after running the instructions in the link I gave. Not sure if you did. Anyway, fixed now and that had little to do with it. ;)

---

### Post by ButterflyKandi on 2016-04-06
I did actually reboot as part of that procedure, but I guess I didn't write that in my reply.  I marked this as solved, and thank you again!

Thanx, -Kandi :P

---

