---
title: "Problem with udev and package installer"
date: 2018-09-08
forum: General Help
---

### Post by virtualis2 on 2018-09-08
Hello everyone. I'm a novice and I stuck with a problem using Ubuntu 16.04 LTS. I used to work in Windows, so my Ubuntu system is almost clean with several installed programs such as Sublime, Chromium and Tweak-Tool. 

The top line of Ubuntu Desktop shows an error which says:

*The error message was: 'Unknown Error: '<class 'System  Error'>' (E:The Package udev needs to be reinstalled, but I can't  find an archive for it.)'. This usually means that your installed  packages have unmet dependencies.*

I tried such commands like *sudo apt-get clean, sudo apt-get update* but it caused no result. If I apply *apt-cache show udev*, then the output is the following:

```
Package: udev
Status: install reinstreq half-configured
Priority: important
Section: admin
Installed-Size: 6727
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: foreign
Source: systemd
Version: 229-4ubuntu12
Config-Version: 229-4ubuntu12
Replaces: bash-completion (<< 1:2.1), systemd (<< 224-2)
Depends:  libacl1 (>= 2.2.51-8), libblkid1 (>= 2.19.1), libc6 (>= 2.17),  libkmod2 (>= 5~), libselinux1 (>= 2.0.65), lsb-base (>=  4.1+Debian11ubuntu7), adduser, libudev1 (= 229-4ubuntu12), util-linux  (>= 2.27.1), procps
Pre-Depends: dpkg (>= 1.17.14)
Breaks:  bash-completion (<< 1:2.1), consolekit (<< 0.4.6-1),  ifupdown (<< 0.8.5~), kmod (<< 14), lvm2 (<<  2.02.133-1ubuntu1), mdadm (<< 3.3-2ubuntu3), plymouth (<<  0.9.0-7), systemd (<< 224-2)
Conffiles:
 /etc/init.d/udev e4da2ae5c153148fad0b3f6e5e7ce61e
 /etc/init/udev.conf 41c0081f3a830e0902aaff76a53edf98
 /etc/init/udevmonitor.conf ec187fc822d47c41416e7c531c8c48dd
 /etc/init/udevtrigger.conf 651ff2421dde80be7ce7ccbf7fa8cf18
 /etc/modprobe.d/fbdev-blacklist.conf 0b9c466830040ec52986cc3ea117bef5
 /etc/udev/udev.conf a9c43ddab6e58eefa56db50ff44b2b46
Description-en: /dev/ and hotplug management daemon
 udev is a daemon which dynamically creates and removes device nodes from
 /dev/, handles hotplug events and loads drivers at boot time.
Description-md5: e875ddb09f46f1f7672af537f0c875ca
Homepage: [http://www.freedesktop.org/wiki/Software/systemd](http://www.freedesktop.org/wiki/Software/systemd)
Original-Maintainer: Debian systemd Maintainers <pkg-systemd-maintainers@lists.alioth.debian.org>
```

```
Package: udev
Priority: required
Section: admin
Installed-Size: 5933
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian systemd Maintainers <pkg-systemd-maintainers@lists.alioth.debian.org>
Architecture: amd64
Source: systemd
Version: 208-8ubuntu8.2
Depends:  libacl1 (>= 2.2.51-8), libblkid1 (>= 2.19.1), libc6 (>= 2.17),  libkmod2 (>= 5~), libselinux1 (>= 2.0.65), libudev1 (=  208-8ubuntu8.2), lsb-base (>= 4.1+Debian11ubuntu7), util-linux (>=  2.16), procps
Pre-Depends: debconf (>= 1.4.69) | debconf-2.0
Breaks: consolekit (<< 0.4.6-1), kmod (<< 14), systemd (<< 208)
Filename: pool/main/s/systemd/udev_208-8ubuntu8.2_amd64.deb
Size: 803512
MD5sum: 36659c044367b694dfa27abfad53a7e2
SHA1: df6655f3f0f4d9e7151f57090390dce06e1b28a7
SHA256: 47c2be7969f679ceaf59b9a8881237788bc4a3b7c0c9b6ff65e3f3d4eaaf53d1
Description-en: /dev/ and hotplug management daemon
 udev is a daemon which dynamically creates and removes device nodes from
 /dev/, handles hotplug events and loads drivers at boot time.
Description-md5: e875ddb09f46f1f7672af537f0c875ca
Multi-Arch: foreign
Homepage: [http://www.freedesktop.org/wiki/Software/systemd](http://www.freedesktop.org/wiki/Software/systemd)
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 9m
Task: minimal

Package: udev
Priority: required
Section: admin
Installed-Size: 5937
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian systemd Maintainers <pkg-systemd-maintainers@lists.alioth.debian.org>
Architecture: amd64
Source: systemd
Version: 208-8ubuntu8
Depends:  libacl1 (>= 2.2.51-8), libblkid1 (>= 2.19.1), libc6 (>= 2.17),  libkmod2 (>= 5~), libselinux1 (>= 2.0.65), libudev1 (=  208-8ubuntu8), lsb-base (>= 4.1+Debian11ubuntu7), util-linux (>=  2.16), procps
Pre-Depends: debconf (>= 1.4.69) | debconf-2.0
Breaks: consolekit (<< 0.4.6-1), kmod (<< 14), systemd (<< 208)
Filename: pool/main/s/systemd/udev_208-8ubuntu8_amd64.deb
Size: 803234
MD5sum: d8741db1938ab0a4f8327b5ef910a4c9
SHA1: 9e08bb787ab7ff7ea4e9f06b536981df0a117572
SHA256: df8fcc56a9c4eb8ec01687a947505d82d04337644ec077e262ee7caad9b6bed5
Description-en: /dev/ and hotplug management daemon
 udev is a daemon which dynamically creates and removes device nodes from
 /dev/, handles hotplug events and loads drivers at boot time.
Description-md5: e875ddb09f46f1f7672af537f0c875ca
Multi-Arch: foreign
Homepage: [http://www.freedesktop.org/wiki/Software/systemd](http://www.freedesktop.org/wiki/Software/systemd)
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 9m
Task: minimal

```
Also, I can't run GDebi because of the next error message:

[I]Software Index is broken

This is a major failure of your  software management system. Please check for broken packages with  synaptic, check the file permissions and correctness of the file  '/etc/apt/sources.list' and reload the software information with: 'sudo  apt-get update' and 'sudo apt-get install -f'.

[/I]If I try[I] [I]sudo apt-get install -f:

```
sudo: unable to resolve host ***
[sudo] password for vs: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package udev needs to be reinstalled, but I can't find an archive for it.[/I]
```
[/I]
It seems like something really bad happened and now I can't install any packages I want using apt-get. Can anyone help please?

---

### Post by deadflowr on 2018-09-08
Seems seriously out of date.
Please run
```
sudo apt update
```
and post back the results.

---

### Post by virtualis2 on 2018-09-08
Done.

[U][B]sudo apt update


[/B][/U]```
Ign:1 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) utopic InRelease                   
Hit:2 [http://ppa.launchpad.net/costales/unity-webapps-telegram/ubuntu](http://ppa.launchpad.net/costales/unity-webapps-telegram/ubuntu) xenial InRelease
Ign:3 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) utopic-updates InRelease           
Hit:4 [http://ppa.launchpad.net/numix/ppa/ubuntu](http://ppa.launchpad.net/numix/ppa/ubuntu) xenial InRelease               
Ign:5 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) utopic-security InRelease    
Ign:6 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) utopic-backports InRelease         
Hit:7 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) utopic Release               
Hit:8 [http://ppa.launchpad.net/peterlevi/ppa/ubuntu](http://ppa.launchpad.net/peterlevi/ppa/ubuntu) xenial InRelease
Hit:9 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) utopic-updates Release             
Hit:11 [http://ppa.launchpad.net/webupd8team/sublime-text-3/ubuntu](http://ppa.launchpad.net/webupd8team/sublime-text-3/ubuntu) xenial InRelease
Hit:12 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) utopic-security Release     
Hit:13 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) utopic-backports Release
Reading package lists... Done                      
Building dependency tree       
Reading state information... Done
5 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

_**apt list --upgradable**_

```
Listing... Done
numix-gtk-theme/xenial,xenial 2.6.7+670~201710270712~ubuntu16.04.1 all [upgradable from: 2.6.5+606~201610230531~ubuntu16.04.1]
numix-icon-theme/xenial,xenial 0.3+931~201804050035~ubuntu16.04.1 all [upgradable from: 0.3+871~201610060517~ubuntu16.04.1]
numix-icon-theme-circle/xenial,xenial 2.0.3+21~201806080916~ubuntu16.04.1 all [upgradable from: 2.0.3+10~201611040016~ubuntu16.04.1]
variety/xenial,xenial 0.6.9~ppa667~ubuntu16.04.1 all [upgradable from: 0.6.3-0~581~201611011859~ubuntu16.04.1]
variety-slideshow/xenial,xenial 0.1-0~23~ubuntu16.04.1 all [upgradable from: 0.1-0~21~ubuntu16.04.1]
```

---

### Post by deadflowr on 2018-09-08
14.10? aka utopic unicorn. very old now.
Best to download a clean copy of 16.04 and nuke the current install and reinstall 16.04 in it's place.
Backup your personal data. 

No use trying to deal with this as it is.
All you're asking for is trouble.

14.10 is several years out of support and I see no good way to upgrade it or to even use it.
14.10 is highly insecure.

More help:
[https://help.ubuntu.com/community/BackupYourSystem]("https://help.ubuntu.com/community/BackupYourSystem")
and
[http://releases.ubuntu.com/16.04/]("http://releases.ubuntu.com/16.04/")

---

### Post by virtualis2 on 2018-09-08
> **deadflowr said:**
> 14.10? aka utopic unicorn. very old now.
Best to download a clean copy of 16.04 and nuke the current install and reinstall 16.04 in it's place.
Backup your personal data. 

No use trying to deal with this as it is.
All you're asking for is trouble.

14.10 is several years out of support and I see no good way to upgrade it or to even use it.
14.10 is highly insecure.

More help:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
and
[http://releases.ubuntu.com/16.04/](http://releases.ubuntu.com/16.04/)

OK, maybe it's the least painful way. Thank you.
BTW, kinda stupid question, anyway, what do you mean by the 14.10 version? The Ubuntu version I have installed is 16.04 LTS as I posted above.

---

