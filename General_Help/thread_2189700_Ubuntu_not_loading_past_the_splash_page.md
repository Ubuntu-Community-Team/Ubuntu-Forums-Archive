---
title: "Ubuntu not loading past the splash page"
date: 2013-11-23
forum: General Help
---

### Post by vasishta94 on 2013-11-23
Hello,

I had a lot of issues/problems, initially it was bootloader not being installed. I had posted about it here: [https://answers.launchpad.net/boot-repair/+question/239697](https://answers.launchpad.net/boot-repair/+question/239697)
I'll post some of the excerpts here:

I seem to have fixed the bootloader issue. I rain the boot-repair and  chose the GRUB Legacy option in a post somewhere by YannUbuntu, and it  said it was successfully repaired - but it directly booted  ubuntu,(couldn't access windows at all) and it didn't go past the Ubuntu  screen(purple, with the logo and 5 dots which sequentially change from  white to orange). I rebooted using the ubuntu install disk, and ran the  boot-repair (without the GRUB Legacy this time) - and it again said that  it was repaired successfully. 
The log file: paste.ubuntu.com/6464964

I rebooted and this time, and the GRUB boot menu showed up, and I could  choose between Ubuntu, Advanced Ubuntu options, and my two windows  partitions. I tried logging into windows and its fine, working normally.  I rebooted and tried going into Ubuntu, but now the same issue is back  where I can't get past the ubuntu purple loading screen. Those 5 loading  dots are constantly changing colour/blinking. Been a while now.  Is  something wrong?

 I pressed the arrow key and it shows this:

* Starting mDNS/DNS-SD daemon [ OK ]
* Starting bluetooth daemon [ OK ]
* Starting startpar bridge for notification of upstart job start/stop [ OK ]
* Stopping startpar bridge for notification of upstart job start/stop [ OK ]
* Starting CUPS printing spooler/server [ OK ]
* Starting startpar bridge for notification of upstart job start/stop [ OK ]
* Starting cups-browsed - Bonjour remote printer browsing daemon [ OK ]
* Stopping startpar bridge for notification of upstart job start/stop [ OK ]

These lines are printed everytime I press the arrow key(and switch between this screen and the ubuntu loading screen) - more like a never-ending loop. This screen doesn't go any further than this.

Please help, I need this fixed ASAP.


Vas

---

### Post by jamesisin on 2013-11-23
Perhaps it relates to your choice of legacy GRUB.  Why not choose current GRUB?

---

### Post by vasishta94 on 2013-11-23
Hello jamesisin,

You might have not read the next line I wrote above. 
I  chose legacy GRUB the first time(after countless attempts at  boot-repairing), but it didn't show me any boot menu and directly loaded  ubuntu(and then stuck at the splash page). 
After that I ran  boot-repair normally(without legacy) and it installed/repaired  properly(perhaps it took it as an upgrade?). This time the boot menu(GRUB 2.00 i think) was  there and I could access Windows, but ubuntu didn't get past the splash  page, and those statements(in the main post) iterated. 

You could read the launchpad link I posted above and it has almost every step I performed..

---

### Post by jamesisin on 2013-11-23
Sorry, I misunderstood.

---

### Post by jamesisin on 2013-11-23
This could be related.

[https://bbs.archlinux.org/viewtopic.php?id=147623](https://bbs.archlinux.org/viewtopic.php?id=147623)

---

### Post by vasishta94 on 2013-11-23
No problem - I did post in a very cluttered fashion, and almost without pauses.

I had Googled a bit about this, and I found: [http://forums.linuxmint.com/viewtopic.php?t=141870&p=750804](http://forums.linuxmint.com/viewtopic.php?t=141870&p=750804)
He seems to have had an issue similar to mine, and according to the second post in that page (where he says "SOLVED BY LAST POST HERE:") and going to the thread he redirected to. In that post, he tells to chroot and run this code:
apt-get install --reinstall dpkg upstart

When I run that, I get this:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 124 not upgraded.
Need to get 2,628 kB of archives.
After this operation, 0 B of additional disk space will be used.
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy/main dpkg i386 1.16.12ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy/main upstart i386 1.10-0ubuntu7
  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.16.12ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.16.12ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/u/upstart/upstart_1.10-0ubuntu7_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/u/upstart/upstart_1.10-0ubuntu7_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


And the console control is returned back to me. Would this be related to my issue?

EDIT:

> **jamesisin said:**
> This could be related.

[https://bbs.archlinux.org/viewtopic.php?id=147623](https://bbs.archlinux.org/viewtopic.php?id=147623)


I looked up that post, I don't think its related to my issue. It  looks like an issue with two hard disks.. My boot menu looks fine - I  can access Windows from it, but when I choose ubuntu, it doesn't go past  the splash page as I said earlier..

---

### Post by jamesisin on 2013-11-23
I thought that thread contained the same GRUB error you reported.  If not, c'est la vie.

I wonder why your live CD is not able to resolve those repositories.  Are they down currently?  (Can you ping them?)  I'm not getting any repository errors when I run apt-get update from here, but I don't see that repo among my output either.  Is that one you added?

Hmmm... I might try to run the available updates.

Either way you could try purging the current installation and then installing it fresh (of dpkg and upstart).

---

### Post by vasishta94 on 2013-11-23
I'm pretty new to linux. So could you please tell how to do that?
As for those repositories, I don't think they're down, I can manually access those links through my browser.

---

### Post by jamesisin on 2013-11-23
It's ok if a repo is unreachable in most cases.  I'm not clear what this repository is so I can't say much more than that.

To run your updates from the command line is pretty easy.  But first I want to make sure you are working with your installed system and not running apt-get merely against your live CD.

Take a look at this and confirm you have chroot'd into your installed system.

[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

Without chroot you would be running all commands against your live CD (which would be rather useless).

Once you have confirmed you are running commands against your installed system then you can run your updates thusly:

```
sudo apt-get update
sudo apt-get upgrade
```

You can presumably just run the same reinstall command you ran previously if you just want to reinstall those packages.

---

### Post by vasishta94 on 2013-11-23
I did chroot. Doesn't look like its downloading anything, though. Here's the log:

> ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# apt-get update
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1) saucy InRelease
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1) saucy Release.gpg
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security InRelease                        
  
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1) saucy Release
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy InRelease                           
  
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-updates InRelease                   
  
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-backports InRelease                 
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy InRelease                               
  
Err [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release.gpg                  
  Could not resolve 'security.ubuntu.com'
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg
  Could not resolve 'extras.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy Release.gpg
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-updates Release.gpg
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) saucy-backports Release.gpg
  Could not resolve 'in.archive.ubuntu.com'
Err cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1) saucy/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1) saucy/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1) saucy/main Translation-en_US
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1) saucy/main Translation-en
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1) saucy/restricted Translation-en_US
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1) saucy/restricted Translation-en
Reading package lists... Done
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy/InRelease](http://in.archive.ubuntu.com/ubuntu/dists/saucy/InRelease)  

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy-updates/InRelease](http://in.archive.ubuntu.com/ubuntu/dists/saucy-updates/InRelease)  

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy-backports/InRelease](http://in.archive.ubuntu.com/ubuntu/dists/saucy-backports/InRelease)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/saucy-security/InRelease](http://security.ubuntu.com/ubuntu/dists/saucy-security/InRelease)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/saucy/InRelease](http://extras.ubuntu.com/ubuntu/dists/saucy/InRelease)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/saucy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/saucy-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1)/dists/saucy/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1)/dists/saucy/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/saucy/Release.gpg)  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/saucy-updates/Release.gpg)  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/saucy-backports/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/saucy-backports/Release.gpg)  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/saucy/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/saucy/Release.gpg)  Could not resolve 'extras.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.



Similar thing came for the apt-get upgrade(I don't think I could copy the entire thing):
> root@ubuntu:/# sudo apt-get upgrade
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  account-plugin-aim account-plugin-jabber account-plugin-salut account-plugin-yahoo apparmor apport apport-gtk at-spi2-core cups cups-bsd
  cups-client cups-common cups-daemon cups-ppdc cups-server-common desktop-file-utils empathy empathy-common file-roller firefox
  firefox-locale-de firefox-locale-es firefox-locale-pt firefox-locale-zh-hans gir1.2-atspi-2.0 gir1.2-dbusmenu-glib-0.4 gir1.2-gtk-3.0
  gir1.2-gudev-1.0 gir1.2-unity-5.0 glib-networking glib-networking-common glib-networking-services gnome-control-center
  gnome-control-center-data gnome-control-center-datetime gnome-keyring gnome-orca gnome-screensaver gnome-settings-daemon hud
  indicator-application indicator-appmenu indicator-datetime indicator-session initramfs-tools initramfs-tools-bin libapparmor-perl
  libapparmor1 libatspi2.0-0 libcups2 libcupscgi1 libcupsimage2 libcupsmime1 libcupsppdc1 libdbusmenu-glib4 libdbusmenu-gtk3-4
  libdbusmenu-gtk4 libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2 libgail-3-0 libglamor0 libglib2.0-0 libglib2.0-bin libglib2.0-data
  libgnome-control-center1 libgpod-common libgpod4 libgtk-3-0 libgtk-3-bin libgtk-3-common libgudev-1.0-0 libhud-client2 libido3-0.1-0
  libindicator3-7 libkpathsea6 liblightdm-gobject-1-0 libmission-control-plugins0 libnss3 libnss3-1d libp11-kit-gnome-keyring
  libpam-gnome-keyring libpam-systemd libprocps0 libsystemd-daemon0 libsystemd-journal0 libsystemd-login0 libudev1 libunity-protocol-private0
  libunity-scopes-json-def-desktop libunity9 libupower-glib1 lightdm linux-libc-dev mcp-account-manager-uoa nautilus-sendto-empathy
  openssh-client procps python-cupshelpers python-ubuntu-sso-client python3-apport python3-distupgrade python3-problem-report
  python3-software-properties python3-update-manager software-properties-common software-properties-gtk ssh-askpass-gnome
  system-config-printer-common system-config-printer-gnome system-config-printer-udev systemd-services telepathy-mission-control-5
  ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk ubuntu-sso-client ubuntu-sso-client-qt udev unity-scopes-runner update-manager
  update-manager-core upower xserver-xorg-glamoregl
124 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 51.6 MB of archives.
After this operation, 1,502 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
********I couldn't copy/paste this area.. 

Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main libsystemd-journal0 i386 204-0ubuntu19
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main ubuntu-sso-client-qt all 13.10-0ubuntu1.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main ubuntu-sso-client all 13.10-0ubuntu1.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main python-ubuntu-sso-client all 13.10-0ubuntu1.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main initramfs-tools all 0.103ubuntu1.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main initramfs-tools-bin i386 0.103ubuntu1.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main libapparmor1 i386 2.8.0-0ubuntu31.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main libapparmor-perl i386 2.8.0-0ubuntu31.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main apparmor i386 2.8.0-0ubuntu31.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main ubuntu-release-upgrader-gtk all 1:0.205.2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main ubuntu-release-upgrader-core all 1:0.205.2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main update-manager all 1:0.194.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main update-manager-core all 1:0.194.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main python3-distupgrade all 1:0.205.2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/main libnss3-1d i386 2:3.15.3-0ubuntu0.13.10.1
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/main libnss3 i386 2:3.15.3-0ubuntu0.13.10.1
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/main lightdm i386 1.8.4-0ubuntu1
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/main openssh-client i386 1:6.2p2-6ubuntu0.1
  Could not resolve 'security.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main python3-update-manager all 1:0.194.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main gir1.2-gtk-3.0 i386 3.8.6-0ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main nautilus-sendto-empathy i386 3.8.4-1ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main mcp-account-manager-uoa i386 3.8.4-1ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main account-plugin-yahoo i386 3.8.4-1ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main account-plugin-salut i386 3.8.4-1ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main account-plugin-jabber i386 3.8.4-1ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main account-plugin-aim i386 3.8.4-1ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main empathy i386 3.8.4-1ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main empathy-common all 3.8.4-1ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main telepathy-mission-control-5 i386 1:5.14.1-1ubuntu6.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main libmission-control-plugins0 i386 1:5.14.1-1ubuntu6.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main python3-problem-report all 2.12.5-0ubuntu2.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main file-roller i386 3.10.1-0ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/main python3-problem-report all 2.12.5-0ubuntu2.1
  Could not resolve 'security.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main gir1.2-atspi-2.0 i386 2.10.1-0ubuntu0.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main gir1.2-gudev-1.0 i386 204-0ubuntu19
  Could not resolve 'in.archive.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/main python3-apport all 2.12.5-0ubuntu2.1
  Could not resolve 'security.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main gir1.2-unity-5.0 i386 7.1.2+13.10.20131010-0ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main gnome-control-center-datetime i386 13.10.0+13.10.20131023.2-0ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main indicator-datetime i386 13.10.0+13.10.20131023.2-0ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main gnome-orca all 3.10.1-0ubuntu0.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main gnome-screensaver i386 3.6.1-0ubuntu7
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main hud i386 13.10.1+13.10.20131031-0ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main indicator-application i386 12.10.1+13.10.20131107-0ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/main apport all 2.12.5-0ubuntu2.1
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/main apport-gtk all 2.12.5-0ubuntu2.1
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/main firefox i386 25.0.1+build1-0ubuntu0.13.10.1
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/main firefox-locale-de i386 25.0.1+build1-0ubuntu0.13.10.1
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/main firefox-locale-es i386 25.0.1+build1-0ubuntu0.13.10.1
  Could not resolve 'security.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main indicator-appmenu i386 13.01.0+13.10.20131031-0ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main indicator-session i386 12.10.5+13.10.20131023.1-0ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main libgpod-common i386 0.8.2-7ubuntu4
  Could not resolve 'in.archive.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/main firefox-locale-pt i386 25.0.1+build1-0ubuntu0.13.10.1
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/main firefox-locale-zh-hans i386 25.0.1+build1-0ubuntu0.13.10.1
  Could not resolve 'security.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main libgtk-3-bin i386 3.8.6-0ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main libkpathsea6 i386 2013.20130529.30792-1ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main liblightdm-gobject-1-0 i386 1.8.4-0ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main python-cupshelpers all 1.4.2+20130920-0ubuntu1.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main software-properties-common all 0.92.28
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main software-properties-gtk all 0.92.28
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main python3-software-properties all 0.92.28
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main system-config-printer-common all 1.4.2+20130920-0ubuntu1.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/main liblightdm-gobject-1-0 i386 1.8.4-0ubuntu1
  Could not resolve 'security.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main system-config-printer-gnome all 1.4.2+20130920-0ubuntu1.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main system-config-printer-udev i386 1.4.2+20130920-0ubuntu1.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main unity-scopes-runner all 7.1.2+13.10.20131010-0ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main upower i386 0.9.22-1ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main xserver-xorg-glamoregl i386 0.5.1-0ubuntu4.2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/main linux-libc-dev i386 3.11.0-13.20
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/main ssh-askpass-gnome i386 1:6.2p2-6ubuntu0.1
  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libd/libdrm/libdrm2_2.4.46-1ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libd/libdrm/libdrm2_2.4.46-1ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/p/procps/libprocps0_3.3.3-2ubuntu9_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/p/procps/libprocps0_3.3.3-2ubuntu9_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/systemd/udev_204-0ubuntu19_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/systemd/udev_204-0ubuntu19_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libudev1_204-0ubuntu19_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libudev1_204-0ubuntu19_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-data_2.38.1-0ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-data_2.38.1-0ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-bin_2.38.1-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-bin_2.38.1-0ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/gnome-control-center-data_3.6.3-0ubuntu45.1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/gnome-control-center-data_3.6.3-0ubuntu45.1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsppdc1_1.7.0~rc1-0ubuntu5.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsppdc1_1.7.0~rc1-0ubuntu5.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsmime1_1.7.0~rc1-0ubuntu5.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsmime1_1.7.0~rc1-0ubuntu5.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.7.0~rc1-0ubuntu5.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.7.0~rc1-0ubuntu5.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupscgi1_1.7.0~rc1-0ubuntu5.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupscgi1_1.7.0~rc1-0ubuntu5.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/p/procps/procps_3.3.3-2ubuntu9_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/p/procps/procps_3.3.3-2ubuntu9_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-daemon_1.7.0~rc1-0ubuntu5.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-daemon_1.7.0~rc1-0ubuntu5.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.7.0~rc1-0ubuntu5.1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.7.0~rc1-0ubuntu5.1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.7.0~rc1-0ubuntu5.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.7.0~rc1-0ubuntu5.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.7.0~rc1-0ubuntu5.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.7.0~rc1-0ubuntu5.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-server-common_1.7.0~rc1-0ubuntu5.1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-server-common_1.7.0~rc1-0ubuntu5.1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-ppdc_1.7.0~rc1-0ubuntu5.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-ppdc_1.7.0~rc1-0ubuntu5.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.7.0~rc1-0ubuntu5.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.7.0~rc1-0ubuntu5.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.7.0~rc1-0ubuntu5.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.7.0~rc1-0ubuntu5.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gtk+3.0/libgtk-3-common_3.8.6-0ubuntu2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gtk+3.0/libgtk-3-common_3.8.6-0ubuntu2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/a/at-spi2-core/libatspi2.0-0_2.10.1-0ubuntu0.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/a/at-spi2-core/libatspi2.0-0_2.10.1-0ubuntu0.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/a/at-spi2-core/at-spi2-core_2.10.1-0ubuntu0.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/a/at-spi2-core/at-spi2-core_2.10.1-0ubuntu0.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gtk+3.0/libgail-3-0_3.8.6-0ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gtk+3.0/libgail-3-0_3.8.6-0ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gtk+3.0/libgtk-3-0_3.8.6-0ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gtk+3.0/libgtk-3-0_3.8.6-0ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libgudev-1.0-0_204-0ubuntu19_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libgudev-1.0-0_204-0ubuntu19_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/u/upower/libupower-glib1_0.9.22-1ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/u/upower/libupower-glib1_0.9.22-1ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-settings-daemon/gnome-settings-daemon_3.8.5-0ubuntu11.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-settings-daemon/gnome-settings-daemon_3.8.5-0ubuntu11.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/libgnome-control-center1_3.6.3-0ubuntu45.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/libgnome-control-center1_3.6.3-0ubuntu45.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libsystemd-login0_204-0ubuntu19_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libsystemd-login0_204-0ubuntu19_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/d/desktop-file-utils/desktop-file-utils_0.21-1ubuntu3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/d/desktop-file-utils/desktop-file-utils_0.21-1ubuntu3_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/gnome-control-center_3.6.3-0ubuntu45.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/gnome-control-center_3.6.3-0ubuntu45.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.38.1-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.38.1-0ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/glib-networking/glib-networking_2.38.1-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/glib-networking/glib-networking_2.38.1-0ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/glib-networking/glib-networking-services_2.38.1-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/glib-networking/glib-networking-services_2.38.1-0ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/glib-networking/glib-networking-common_2.38.1-0ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/glib-networking/glib-networking-common_2.38.1-0ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libsystemd-daemon0_204-0ubuntu19_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libsystemd-daemon0_204-0ubuntu19_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libpam-systemd_204-0ubuntu19_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libpam-systemd_204-0ubuntu19_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/systemd/systemd-services_204-0ubuntu19_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/systemd/systemd-services_204-0ubuntu19_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-keyring/libp11-kit-gnome-keyring_3.8.2-0ubuntu3.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-keyring/libp11-kit-gnome-keyring_3.8.2-0ubuntu3.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-keyring/gnome-keyring_3.8.2-0ubuntu3.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-keyring/gnome-keyring_3.8.2-0ubuntu3.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libd/libdbusmenu/gir1.2-dbusmenu-glib-0.4_12.10.3+13.10.20131104-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libd/libdbusmenu/gir1.2-dbusmenu-glib-0.4_12.10.3+13.10.20131104-0ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libd/libdbusmenu/libdbusmenu-glib4_12.10.3+13.10.20131104-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libd/libdbusmenu/libdbusmenu-glib4_12.10.3+13.10.20131104-0ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libd/libdbusmenu/libdbusmenu-gtk3-4_12.10.3+13.10.20131104-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libd/libdbusmenu/libdbusmenu-gtk3-4_12.10.3+13.10.20131104-0ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libd/libdbusmenu/libdbusmenu-gtk4_12.10.3+13.10.20131104-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libd/libdbusmenu/libdbusmenu-gtk4_12.10.3+13.10.20131104-0ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libd/libdrm/libdrm-intel1_2.4.46-1ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libd/libdrm/libdrm-intel1_2.4.46-1ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libd/libdrm/libdrm-nouveau2_2.4.46-1ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libd/libdrm/libdrm-nouveau2_2.4.46-1ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libd/libdrm/libdrm-radeon1_2.4.46-1ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libd/libdrm/libdrm-radeon1_2.4.46-1ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/glamor-egl/libglamor0_0.5.1-0ubuntu4.2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/glamor-egl/libglamor0_0.5.1-0ubuntu4.2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libg/libgpod/libgpod4_0.8.2-7ubuntu4_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libg/libgpod/libgpod4_0.8.2-7ubuntu4_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/h/hud/libhud-client2_13.10.1+13.10.20131031-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/h/hud/libhud-client2_13.10.1+13.10.20131031-0ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/i/ido/libido3-0.1-0_13.10.0+13.10.20131031-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/i/ido/libido3-0.1-0_13.10.0+13.10.20131031-0ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libi/libindicator/libindicator3-7_12.10.2+13.10.20130913-0ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libi/libindicator/libindicator3-7_12.10.2+13.10.20130913-0ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.15.3-0ubuntu0.13.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.15.3-0ubuntu0.13.10.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3_3.15.3-0ubuntu0.13.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3_3.15.3-0ubuntu0.13.10.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-keyring/libpam-gnome-keyring_3.8.2-0ubuntu3.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-keyring/libpam-gnome-keyring_3.8.2-0ubuntu3.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libu/libunity/libunity-scopes-json-def-desktop_7.1.2+13.10.20131010-0ubuntu2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libu/libunity/libunity-scopes-json-def-desktop_7.1.2+13.10.20131010-0ubuntu2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libu/libunity/libunity-protocol-private0_7.1.2+13.10.20131010-0ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libu/libunity/libunity-protocol-private0_7.1.2+13.10.20131010-0ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libu/libunity/libunity9_7.1.2+13.10.20131010-0ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libu/libunity/libunity9_7.1.2+13.10.20131010-0ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/lightdm/lightdm_1.8.4-0ubuntu1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/lightdm/lightdm_1.8.4-0ubuntu1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libsystemd-journal0_204-0ubuntu19_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libsystemd-journal0_204-0ubuntu19_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-sso-client/ubuntu-sso-client-qt_13.10-0ubuntu1.1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-sso-client/ubuntu-sso-client-qt_13.10-0ubuntu1.1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-sso-client/ubuntu-sso-client_13.10-0ubuntu1.1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-sso-client/ubuntu-sso-client_13.10-0ubuntu1.1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-sso-client/python-ubuntu-sso-client_13.10-0ubuntu1.1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-sso-client/python-ubuntu-sso-client_13.10-0ubuntu1.1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools_0.103ubuntu1.1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools_0.103ubuntu1.1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools-bin_0.103ubuntu1.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools-bin_0.103ubuntu1.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor1_2.8.0-0ubuntu31.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor1_2.8.0-0ubuntu31.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor-perl_2.8.0-0ubuntu31.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor-perl_2.8.0-0ubuntu31.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor_2.8.0-0ubuntu31.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor_2.8.0-0ubuntu31.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_6.2p2-6ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_6.2p2-6ubuntu0.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-release-upgrader/ubuntu-release-upgrader-gtk_0.205.2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-release-upgrader/ubuntu-release-upgrader-gtk_0.205.2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-release-upgrader/ubuntu-release-upgrader-core_0.205.2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-release-upgrader/ubuntu-release-upgrader-core_0.205.2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.194.1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.194.1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.194.1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.194.1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-release-upgrader/python3-distupgrade_0.205.2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-release-upgrader/python3-distupgrade_0.205.2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/python3-update-manager_0.194.1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/python3-update-manager_0.194.1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gtk+3.0/gir1.2-gtk-3.0_3.8.6-0ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gtk+3.0/gir1.2-gtk-3.0_3.8.6-0ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_3.8.4-1ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_3.8.4-1ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/e/empathy/mcp-account-manager-uoa_3.8.4-1ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/e/empathy/mcp-account-manager-uoa_3.8.4-1ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/e/empathy/account-plugin-yahoo_3.8.4-1ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/e/empathy/account-plugin-yahoo_3.8.4-1ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/e/empathy/account-plugin-salut_3.8.4-1ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/e/empathy/account-plugin-salut_3.8.4-1ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/e/empathy/account-plugin-jabber_3.8.4-1ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/e/empathy/account-plugin-jabber_3.8.4-1ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/e/empathy/account-plugin-aim_3.8.4-1ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/e/empathy/account-plugin-aim_3.8.4-1ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy_3.8.4-1ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy_3.8.4-1ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy-common_3.8.4-1ubuntu2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy-common_3.8.4-1ubuntu2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/t/telepathy-mission-control-5/telepathy-mission-control-5_5.14.1-1ubuntu6.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/t/telepathy-mission-control-5/telepathy-mission-control-5_5.14.1-1ubuntu6.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/t/telepathy-mission-control-5/libmission-control-plugins0_5.14.1-1ubuntu6.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/t/telepathy-mission-control-5/libmission-control-plugins0_5.14.1-1ubuntu6.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apport/python3-problem-report_2.12.5-0ubuntu2.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apport/python3-problem-report_2.12.5-0ubuntu2.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apport/python3-apport_2.12.5-0ubuntu2.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apport/python3-apport_2.12.5-0ubuntu2.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apport/apport_2.12.5-0ubuntu2.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apport/apport_2.12.5-0ubuntu2.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apport/apport-gtk_2.12.5-0ubuntu2.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apport/apport-gtk_2.12.5-0ubuntu2.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/f/file-roller/file-roller_3.10.1-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/f/file-roller/file-roller_3.10.1-0ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_25.0.1+build1-0ubuntu0.13.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_25.0.1+build1-0ubuntu0.13.10.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-de_25.0.1+build1-0ubuntu0.13.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-de_25.0.1+build1-0ubuntu0.13.10.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-es_25.0.1+build1-0ubuntu0.13.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-es_25.0.1+build1-0ubuntu0.13.10.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-pt_25.0.1+build1-0ubuntu0.13.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-pt_25.0.1+build1-0ubuntu0.13.10.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-zh-hans_25.0.1+build1-0ubuntu0.13.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-zh-hans_25.0.1+build1-0ubuntu0.13.10.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/a/at-spi2-core/gir1.2-atspi-2.0_2.10.1-0ubuntu0.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/a/at-spi2-core/gir1.2-atspi-2.0_2.10.1-0ubuntu0.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/systemd/gir1.2-gudev-1.0_204-0ubuntu19_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/systemd/gir1.2-gudev-1.0_204-0ubuntu19_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libu/libunity/gir1.2-unity-5.0_7.1.2+13.10.20131010-0ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libu/libunity/gir1.2-unity-5.0_7.1.2+13.10.20131010-0ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/i/indicator-datetime/gnome-control-center-datetime_13.10.0+13.10.20131023.2-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/i/indicator-datetime/gnome-control-center-datetime_13.10.0+13.10.20131023.2-0ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/i/indicator-datetime/indicator-datetime_13.10.0+13.10.20131023.2-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/i/indicator-datetime/indicator-datetime_13.10.0+13.10.20131023.2-0ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-orca/gnome-orca_3.10.1-0ubuntu0.1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-orca/gnome-orca_3.10.1-0ubuntu0.1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-screensaver/gnome-screensaver_3.6.1-0ubuntu7_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-screensaver/gnome-screensaver_3.6.1-0ubuntu7_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/h/hud/hud_13.10.1+13.10.20131031-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/h/hud/hud_13.10.1+13.10.20131031-0ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/i/indicator-application/indicator-application_12.10.1+13.10.20131107-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/i/indicator-application/indicator-application_12.10.1+13.10.20131107-0ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/i/indicator-appmenu/indicator-appmenu_13.01.0+13.10.20131031-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/i/indicator-appmenu/indicator-appmenu_13.01.0+13.10.20131031-0ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/i/indicator-session/indicator-session_12.10.5+13.10.20131023.1-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/i/indicator-session/indicator-session_12.10.5+13.10.20131023.1-0ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libg/libgpod/libgpod-common_0.8.2-7ubuntu4_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libg/libgpod/libgpod-common_0.8.2-7ubuntu4_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gtk+3.0/libgtk-3-bin_3.8.6-0ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gtk+3.0/libgtk-3-bin_3.8.6-0ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/t/texlive-bin/libkpathsea6_2013.20130529.30792-1ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/t/texlive-bin/libkpathsea6_2013.20130529.30792-1ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/lightdm/liblightdm-gobject-1-0_1.8.4-0ubuntu1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/lightdm/liblightdm-gobject-1-0_1.8.4-0ubuntu1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_3.11.0-13.20_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_3.11.0-13.20_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/python-cupshelpers_1.4.2+20130920-0ubuntu1.1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/python-cupshelpers_1.4.2+20130920-0ubuntu1.1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/software-properties/software-properties-common_0.92.28_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/software-properties/software-properties-common_0.92.28_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/software-properties/software-properties-gtk_0.92.28_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/software-properties/software-properties-gtk_0.92.28_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/software-properties/python3-software-properties_0.92.28_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/software-properties/python3-software-properties_0.92.28_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_6.2p2-6ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_6.2p2-6ubuntu0.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/system-config-printer-common_1.4.2+20130920-0ubuntu1.1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/system-config-printer-common_1.4.2+20130920-0ubuntu1.1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/system-config-printer-gnome_1.4.2+20130920-0ubuntu1.1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/system-config-printer-gnome_1.4.2+20130920-0ubuntu1.1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/system-config-printer-udev_1.4.2+20130920-0ubuntu1.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/system-config-printer-udev_1.4.2+20130920-0ubuntu1.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libu/libunity/unity-scopes-runner_7.1.2+13.10.20131010-0ubuntu2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libu/libunity/unity-scopes-runner_7.1.2+13.10.20131010-0ubuntu2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/u/upower/upower_0.9.22-1ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/u/upower/upower_0.9.22-1ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/glamor-egl/xserver-xorg-glamoregl_0.5.1-0ubuntu4.2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/glamor-egl/xserver-xorg-glamoregl_0.5.1-0ubuntu4.2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@u

There's a small place in between there where I couldn't copy - its just after where it asked me to install or not (Y/n).

---

### Post by vasishta94 on 2013-11-23
Also, I could ping to in.archive.ubuntu.com through the terminal(ubuntu, not chroot). However if I chroot, and then try to ping, it says:
> ping: unknown host in.archive.ubuntu.com


Also, just for testing purposes, I tried the sudo apt-get update from non-root(that is, ubuntu@ubuntu:~$ ) and the update seems to run fine, without the error of resolving the in.archive domain. I didn't try, but I don't think this would fix my issue because as you said this would update the live CD which would be useless?

So by the looks of it, the root/chroot is not able to do it.
Maybe that has something to do with this?

---

### Post by vasishta94 on 2013-11-23
<deleted>

---

### Post by jamesisin on 2013-11-23
It sounds like your live system doesn't have a network connection.  Are you running wirelessly?  You may want to attach to a wire to get through this.

```
$ ping in.archive.ubuntu.com
PING in.archive.ubuntu.com (91.189.92.201) 56(84) bytes of data.
64 bytes from urayuli.canonical.com (91.189.92.201): icmp_seq=1 ttl=49 time=317 ms
64 bytes from urayuli.canonical.com (91.189.92.201): icmp_seq=2 ttl=49 time=271 ms
^C
--- in.archive.ubuntu.com ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 2000ms
rtt min/avg/max/mdev = 271.763/294.840/317.917/23.077 ms
```

---

### Post by vasishta94 on 2013-11-23
I realized I hadn't done this step in the chroot:
> Mount the critical virtual filesystems. Run the following as a single command: for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
[step 8 in here: [https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot](https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot) ]
Was reading about some resolv.cnf 

Now it looks like the update is running. I'll run all of them and let you know.

---

### Post by vasishta94 on 2013-11-23
Guess what - it worked like a charm. :)
I ran the apt-get update, upgrade and just in case i needed to, reinstalled the dpkg and upstart. 13.10 works now. Do you know a proper guide as such to the next few things I should do after installing this?

Thank you so much for your help and time. :) Isn't there any place here where I can +rep you?

Cheers,
Vas

---

### Post by jamesisin on 2013-11-23
When I run updates I also run these to clean things up a bit.

```
sudo apt-get autoremove
sudo apt-get autoclean
```

I think when you run upgrade it automatically runs a grub update but this won't hurt.

```
sudo update-grub
```

Other than that, if your system is now booting correctly I'd say you are good to go.

---

