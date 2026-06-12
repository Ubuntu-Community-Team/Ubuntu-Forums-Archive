---
title: "cant run sudo apt upgrade ubuntu 16.04.3"
date: 2018-02-21
forum: General Help
---

### Post by sic698 on 2018-02-21
Hi,

Im running ubuntu 16.04.3 and cant upgrade with sudo apt upgrade I get the following errors which than puts my system into read-only file system

sudo apt upgrade 

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 


I then run this command sudo dpkg --configure and after a few mins I get the following error

dpkg:error processing package linux-firmware (--configure)

subprocess installed post-installation script returned error exit status 1



The kernel that im currently running is 4.4.0-116-generic

It seems to crash when update kernel 4.4.0-103

---

### Post by ubname on 2018-02-21
I would try to remove linux-firmware, update and reinstall it ...


```
sudo apt remove --purge linux-firmware

sudo dpkg --configure  -a

sudo apt update

sudo apt upgrade
```

---

### Post by sic698 on 2018-02-21
I cant get past the 1st command without the dpkg error


> ~$ sudo apt remove --purge linux-firmware
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by Impavidus on 2018-02-21
The full output of those commands may help. The root cause of your problem must be hidden in it somewhere.

Once you have 4.4.0-116, there should be no need for 4.4.0-103 (which, if I'm not mistaken, was broken anyway). The way these kernel-related upgrades are handled on Ubuntu is that a new package alongside the old one, not an in-place upgrade of the old package.

---

### Post by sic698 on 2018-02-21
```
:~$ sudo dpkg --configure -a
Setting up linux-firmware (1.157.17) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-116-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-112-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-104-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-112-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-112-genericupdate-initramfs: 
Generating /boot/initrd.img-4.4.0-103-generic
mkdir: cannot create directory &#8216;/var/tm
/boot/initrd.img-4.4.0-103-generic
mkdir: cannot create directory &#8216;/var/tmp/mkinitramfs_s4SLOc//lib/modules/4.4.0-103-generic/kernel&#8217;: Read-only file system
cp: cannot create regular file '/var/tmp/mkinitramfs_s4SLOc//lib/modules/4.4.0-103-generic/kernel/drivers/usb/storage/usb-storage.ko': No such file or directory
mkdir: cannot create directory &#8216;/var/tmp/mkinitramfs_s4SLOc//lib/modules/4.4.0-103-generic/kernel&#8217;: Read-only file system
cp: cannot create regular file '/var/tmp/mkinitramfs_s4SLOc//lib/modules/4.4.0-103-generic/kernel/drivers
dpkg: error processing package linux-firmware (--configure):
subprocess installed post-installation script returned error exit status 1
Setting up libcups2:amd64 (2.1.3-4ubuntu0.4) ...
dpkg: unrecoverable fatal error, aborting:
unable to flush updated status of 'libc-bin': Read-only file system

```


This is my output and I shortened it but those are some of the errors that I get, My kernel crashes turns my ubuntu into read-only I have to reboot the computer run a fsck -y /dev/sda* to fix the crashed kernel then it boots into ubuntu 16.04

---

### Post by #&amp;thj^% on 2018-02-21
This is just a common response but make sure you back-up what you need first, off the Disk.

Try deleting the lock file i.e

```
sudo rm /var/lib/dpkg/lock
```

and then run

```
sudo dpkg --reconfigure -a
```

and then:

```
sudo apt update
```

This is caused by when software upgrades is some how interrupted.

---

### Post by sic698 on 2018-02-21
thanks guys, I ran all the commands in this thread including the last one which seemed to have solved the issues with deblocking dkpg.

everything is resolved 

have a great day :)

---

### Post by sic698 on 2018-02-21
Hi Guys 

heres an update my wifi stopped working 

```
[   91.415359] iwlwifi 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   92.129303] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-6000-6.ucode failed with error -2
[   92.129333] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-6000-5.ucode failed with error -2
[   92.138454] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-6000-4.ucode failed with error -2
[   92.138457] iwlwifi 0000:02:00.0: request for firmware file 'iwlwifi-6000-4.ucode' failed.
[   92.139437] iwlwifi 0000:02:00.0: no suitable firmware found!
keypass@DEFCON5:/tmp$ sudo modprobe iwlwifi && dmesg | grep iwl 
[   91.415359] iwlwifi 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   92.129303] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-6000-6.ucode failed with error -2
[   92.129333] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-6000-5.ucode failed with error -2
[   92.138454] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-6000-4.ucode failed with error -2
[   92.138457] iwlwifi 0000:02:00.0: request for firmware file 'iwlwifi-6000-4.ucode' failed.
[   92.139437] iwlwifi 0000:02:00.0: no suitable firmware found!


```


And... my sudo apt updates and upgrade still do not work properly heres what I get as a message

```
:~$ sudo apt update
Hit:1 http://ppa.launchpad.net/jonathonf/firefox-esr/ubuntu xenial InRelease
Hit:2 http://archive.ubuntu.com/ubuntu xenial InRelease
Hit:3 http://archive.ubuntu.com/ubuntu xenial-security InRelease
Hit:4 http://archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:5 http://archive.ubuntu.com/ubuntu xenial-proposed InRelease
Hit:6 http://archive.ubuntu.com/ubuntu xenial-backports InRelease
Reading package lists... Done                     
Building dependency tree       
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.


```

```
$ sudo apt upgrade
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

```
:~$ sudo dpkg --configure -a
```

```
sudo apt upgrade
```

```
~$ sudo apt upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libqmi-glib1 thermald
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  gnome-terminal gnome-terminal-data
The following packages will be upgraded:
  libgcrypt20 libgcrypt20:i386
2 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 659 kB/36.7 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 

et:1 http://archive.ubuntu.com/ubuntu xenial-proposed/main i386 libgcrypt20 i386 1.6.5-2ubuntu0.4 [321 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libgcrypt20 amd64 1.6.5-2ubuntu0.4 [337 kB]
Fetched 659 kB in 1s (636 kB/s)      
(Reading database ... 519376 files and directories currently installed.)
Preparing to unpack .../libgcrypt20_1.6.5-2ubuntu0.4_amd64.deb ...
De-configuring libgcrypt20:i386 (1.6.5-2ubuntu0.3) ...
Unpacking libgcrypt20:amd64 (1.6.5-2ubuntu0.4) over (1.6.5-2ubuntu0.3) ...
Preparing to unpack .../libgcrypt20_1.6.5-2ubuntu0.4_i386.deb ...
Unpacking libgcrypt20:i386 (1.6.5-2ubuntu0.4) over (1.6.5-2ubuntu0.3) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
dpkg: error processing package linux-image-extra-4.4.0-103-generic (--configure):
 package linux-image-extra-4.4.0-103-generic is not ready for configuration
 cannot configure (current status 'half-installed')
Setting up libgcrypt20:i386 (1.6.5-2ubuntu0.4) ...
Setting up libgcrypt20:amd64 (1.6.5-2ubuntu0.4) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Errors were encountered while processing:
 linux-image-extra-4.4.0-103-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

```
dpkg: error processing package linux-image-extra-4.4.0-103-generic (--configure):
 package linux-image-extra-4.4.0-103-generic is not ready for configuration
 cannot configure (current status 'half-installed')
Errors were encountered while processing:
 linux-image-extra-4.4.0-103-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by #&amp;thj^% on 2018-02-21
Is there a real reason you need xenial-proposed enabled? (Usually not recommended)

---

### Post by sic698 on 2018-02-21
I'm not sure what you mean by that but thats what configured in my servers.

---

### Post by #&amp;thj^% on 2018-02-21
proposed is not enabled by default...
What does this show?
```
cat /etc/apt/sources.list
```

---

### Post by sic698 on 2018-02-21
```
###### Ubuntu Main Repos
deb http://archive.ubuntu.com/ubuntu xenial main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial main restricted universe multiverse

###### Ubuntu Update Repos
deb http://archive.ubuntu.com/ubuntu xenial-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu xenial-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu xenial-proposed main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-proposed main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse
```

---

### Post by #&amp;thj^% on 2018-02-21
Well you have everything enabled...including the kitchen sink. :D
```
deb http://archive.ubuntu.com/ubuntu xenial-proposed main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-proposed main restricted universe multiverse
```
How Old is this install? I "might" be able to help if it is not more than a couple of months old.
Factory Repos Look like the below:
```
#deb cdrom:[Ubuntu-Studio 16.04.3 LTS _Xenial Xerus_ - Release amd64 (20170801)]/ xenial main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
```

---

### Post by sic698 on 2018-02-21
this install is less then 1 years old, I've removed prepose from the list.

---

### Post by #&amp;thj^% on 2018-02-21
> **sic698 said:**
> this install is less then 1 years old, I've removed prepose from the list.

That's older than just a couple of months then. (Yuck!)
This will be a long and frustrating fix, and NO Guaranty your system will be intact with the process.
So let me know.:)

---

### Post by sic698 on 2018-02-21
Yes I am interested in fixing this system I have no intentions of formatting and reinstall.

---

### Post by #&amp;thj^% on 2018-02-21
1.Make sure you removed the entries of -proposed or -backports in your /etc/apt/sources.list and /etc/apt/sources.list.d/* files.

2.As Root Add an "apt-preferences" file, e.g: (/etc/apt/preferences.d/99-back-to-stable-updates" containing:
```
Package: *
Pin: release a=xenial
Pin-Priority: 1001

Package: *
Pin: release a=xenial-updates
Pin-Priority: 1001

Package: *
Pin: release a=xenial-security
Pin-Priority: 1001

Package: *
Pin: release a=xenial-proposed
Pin-Priority: -10

Package: *
Pin: release a=xenial-backports
Pin-Priority: -10

``` 
The pinning of > 1000 will make apt force a downgrade on packages from that channel and a priority of < 0 on the -proposed and -backports channels will make it remove any additional packages too.
3.Now Run:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
If all went well then, Inspect the output apt will give you, and if you think it's okay, then accept it. If you need to check on why and what version it will be downgraded to, check this with apt-cache policy packagename to see what versions are available and what apt decides is the candidate for installation.
**When all is good again you can now Remove the** "/etc/apt/preferences.d/99-back-to-stable-updates" file again, as it's not needed anymore.
```
sudo rm /etc/apt/preferences.d/99-back-to-stable-updates
```
Fingers and Toe's crossed. ;)

---

### Post by deadflowr on 2018-02-21
Which kernel is currently being booted:
```
uname -r
```
and what's the status of the  linux-image-extra-4.4.0-103-generic package?
```
dpkg -l linux-image*
```

---

### Post by sic698 on 2018-02-21
> **1fallen said:**
> 1.Make sure you removed the entries of -proposed or -backports in your /etc/apt/sources.list and /etc/apt/sources.list.d/* files.

2.As Root Add an "apt-preferences" file, e.g: (/etc/apt/preferences.d/99-back-to-stable-updates" containing:
```
Package: *
Pin: release a=xenial
Pin-Priority: 1001

Package: *
Pin: release a=xenial-updates
Pin-Priority: 1001

Package: *
Pin: release a=xenial-security
Pin-Priority: 1001

Package: *
Pin: release a=xenial-proposed
Pin-Priority: -10

Package: *
Pin: release a=xenial-backports
Pin-Priority: -10

``` 
The pinning of > 1000 will make apt force a downgrade on packages from that channel and a priority of < 0 on the -proposed and -backports channels will make it remove any additional packages too.
3.Now Run:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
If all went well then, Inspect the output apt will give you, and if you think it's okay, then accept it. If you need to check on why and what version it will be downgraded to, check this with apt-cache policy packagename to see what versions are available and what apt decides is the candidate for installation.
**When all is good again you can now Remove the** "/etc/apt/preferences.d/99-back-to-stable-updates" file again, as it's not needed anymore.
```
sudo rm /etc/apt/preferences.d/99-back-to-stable-updates
```
Fingers and Toe's crossed. ;)

so far so good after the reboot :) , my wifi is back and working however I'm still having issues with sudo apt upgrade in terminal.

---

### Post by sic698 on 2018-02-21
> **deadflowr said:**
> Which kernel is currently being booted:
```
uname -r
```
and what's the status of the  linux-image-extra-4.4.0-103-generic package?
```
dpkg -l linux-image*
```


```
~$ uname -r
4.4.0-116-generic


```

```
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  linux-image    <none>       <none>       (no description available)
rc  linux-image-4. 4.4.0-102.12 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-103.12 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-104.12 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-112.13 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-116.14 amd64        Linux kernel image for version 4.
rc  linux-image-ex 4.4.0-102.12 amd64        Linux kernel extra modules for ve
rH  linux-image-ex 4.4.0-103.12 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-104.12 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-112.13 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-116.14 amd64        Linux kernel extra modules for ve


```

---

### Post by #&amp;thj^% on 2018-02-21
> **sic698 said:**
> so far so good after the reboot :) , my wifi is back and working however I'm still having issues with sudo apt upgrade in terminal.
Well some success then.:) Please show the errors here, as they contain information that help.
It's not a read only error is it?

---

### Post by deadflowr on 2018-02-21
Try the basic idea from here:
[https://askubuntu.com/questions/59261/dpkg-cannot-remove-package-linux-restricted-modules]("https://askubuntu.com/questions/59261/dpkg-cannot-remove-package-linux-restricted-modules")
But change it to your linux-image-extra-4.4.0-103-generic.postrm

---

### Post by sic698 on 2018-02-21
```
~$ sudo apt upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libampache-browser libcrossguid1 liblua5.3-0 libplatform2 libqt5concurrent5 python-bluez
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  gnome-terminal gnome-terminal-data
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0 B/36.0 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg: error processing package linux-image-extra-4.4.0-103-generic (--configure):
 package linux-image-extra-4.4.0-103-generic is not ready for configuration
 cannot configure (current status 'half-installed')
Errors were encountered while processing:
 linux-image-extra-4.4.0-103-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

this is where im stuck with the sudo apt upgrade

---

### Post by #&amp;thj^% on 2018-02-21
> **deadflowr said:**
> Try the basic idea from here:
[https://askubuntu.com/questions/59261/dpkg-cannot-remove-package-linux-restricted-modules]("https://askubuntu.com/questions/59261/dpkg-cannot-remove-package-linux-restricted-modules")
But change it to your linux-image-extra-4.4.0-103-generic.postrm

+1 ;)

---

### Post by sic698 on 2018-02-21
it sounds great except my linux image file is not found in that folder ?

---

### Post by #&amp;thj^% on 2018-02-21
Give this a go:
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
```
Show any errors here.

---

### Post by sic698 on 2018-02-21
> **1fallen said:**
> Give this a go:
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get clean
sudo apt-get dist-update
```
Show any errors here.

:~$ sudo rm -rf /var/lib/apt/lists/*
~$ sudo apt-get clean
~$ sudo apt-get dist-update
E: Invalid operation dist-update

---

### Post by deadflowr on 2018-02-21
What's
```
ls /var/lib/dpkg/info | grep linux-image-extra
```
show?

Also, worse case, try reinstalling the package.

---

### Post by sic698 on 2018-02-21
> **deadflowr said:**
> What's
```
ls /var/lib/dpkg/info | grep linux-image-extra
```
show?

Also, worse case, try reinstalling the package.
```
:~$ ls /var/lib/dpkg/info | grep linux-image-extra
linux-image-extra-4.4.0-102-generic.list
linux-image-extra-4.4.0-102-generic.postrm
linux-image-extra-4.4.0-103-generic.list
linux-image-extra-4.4.0-103-generic.md5sums
linux-image-extra-4.4.0-103-generic.postinst
linux-image-extra-4.4.0-103-generic.postrm
linux-image-extra-4.4.0-104-generic.list
linux-image-extra-4.4.0-104-generic.md5sums
linux-image-extra-4.4.0-104-generic.postinst
linux-image-extra-4.4.0-104-generic.postrm
linux-image-extra-4.4.0-112-generic.list
linux-image-extra-4.4.0-112-generic.md5sums
linux-image-extra-4.4.0-112-generic.postinst
linux-image-extra-4.4.0-112-generic.postrm
linux-image-extra-4.4.0-116-generic.list
linux-image-extra-4.4.0-116-generic.md5sums
linux-image-extra-4.4.0-116-generic.postinst
linux-image-extra-4.4.0-116-generic.postrm


```

---

### Post by #&amp;thj^% on 2018-02-21
> **sic698 said:**
> :~$ sudo rm -rf /var/lib/apt/lists/*
~$ sudo apt-get clean
~$ sudo apt-get dist-update
E: Invalid operation dist-update

Sorry about that, too big a hurray today!:D I fixed the code in post#26
And after try deadflowr's suggestion.
EDIT: @sic698 requesting feedback here.

---

### Post by sic698 on 2018-02-25
Hi fallen,

I followed your post on post 26 and I was able to upgrade ubuntu to 16.04.4 however now when I boot into my desktop, I fall into a terminal window for 2 seconds displaying ubuntu 16.04.4 and then a black screen with a flashing cursor/line, Also my screen flickers for a couple of seconds trying to load my desktop.

seems like my desktop crashed ?

---

### Post by #&amp;thj^% on 2018-02-25
Is there anything interesting in:
```
dmesg
```

---

