---
title: "Software Updater Lockup"
date: 2016-06-23
forum: General Help
---

### Post by The00Dustin on 2016-06-23
Yesterday, I let Software Updater start installing updates.  It locked up (turned gray) on "Setting up grub-pc (2.02-beta2-9ubuntu1.8) ..." and has stayed there for well over 24 hours.  For obvious reasons, I'm afraid this will leave my system unbootable, so I'm looking for advice on how I should proceed.  I can still see on the screen that update-initramfs ran and a new grub configuration file was generated.  I can also see that grub-common, grub2-common, and grub-pc-bin have already updated.  How should I proceed here?

---

### Post by deadflowr on 2016-06-23
Somewhere (perhaps in another workspace?) there should have been a pop-up window for grub-pc stating that a newer configuration file can be installed.
It would have asked you if you wanted to install the new version of that configuration file, or keep the one currently being used.

What you might do to see if there is indeed a pop-up window hiding somewhere is to use the window switcher mechanism alt+tab > up/down key.
(To view all workspaces, use ctrl + alt + tab > up/down key.)
You use the up/down keys to view apps that may have multiple windows, since alt+tab will only show a single in the default viewer.
(If that makes any sense)

---

### Post by The00Dustin on 2016-06-27
> **deadflowr said:**
> Somewhere (perhaps in another workspace?) there should have been a pop-up window for grub-pc stating that a newer configuration file can be installed.
It would have asked you if you wanted to install the new version of that configuration file, or keep the one currently being used.

What you might do to see if there is indeed a pop-up window hiding somewhere is to use the window switcher mechanism alt+tab > up/down key.
(To view all workspaces, use ctrl + alt + tab > up/down key.)
You use the up/down keys to view apps that may have multiple windows, since alt+tab will only show a single in the default viewer.
(If that makes any sense)Well, apparently e-mail notifications aren't working for me, but I just tried the above suggestions and can add the following:
Alt+Tab only shows Software Updater and Desktop
Ctrl+Alt+Tab only shows Software Updater and Desktop
Ctrl+Alt+(1-6) each only show the login screen for their respective shells

I also tried minimizing and restoring the Software Updater window to see if another window was behind it even if Alt+Tab woudn't show it, and there was never one visible during those steps.  What next?  Should I use kill to send any particular command to any particular process or do we need to focus on how to recover if a reboot leads to an unbootable situation?

---

### Post by The00Dustin on 2016-06-27
ETA:  Because I didn't originally specify as much, I did use up/down keys during alt+tab prior to trying the minimize and restore functions.  I only saw the main Software Updater window during that process (no other windows appeared to be available with multiple down or up presses).

---

### Post by banceu_sergiu_ione on 2016-06-27
Still there after 3 days ?
If yes, can you put the output of:
```
lsb_release -a
```

---

### Post by deadflowr on 2016-06-27
Hmm, you seem to have a similar problem to this bug:
[lpbug]1457353[/lpbug]

FYI, the grub-pc package at issue is for 14.04.

---

### Post by The00Dustin on 2016-06-28
> **banceu_sergiu_ione said:**
> Still there after 3 days ?If yes, can you put the output of:```
lsb_release -a
```From a remote shell:```
$ lsb_release -aNo LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:        14.04
Codename:       trusty
```> **deadflowr said:**
> Hmm, you seem to have a similar problem to this bug:
[lpbug]1457353[/lpbug]

FYI, the grub-pc package at issue is for 14.04.I agree, it looks quite similar.  So perhaps running the appropriate grub command before restarting would prevent me from needing to re-install Ubuntu?  Would that be update-grub? update-grub2?  Some other command?  Would parameters be necessary?  Obviously installing [COLOR=#333333][FONT=monospace]libgtk2-perl[/FONT][/COLOR] would make sense after dealing with the issue at hand, as it doesn't appear to be installed:```
$ apt list --installed | grep libgtk2

WARNING: apt does not have a stable CLI interface yet. Use with caution in scripts.


libgtk2.0-0/trusty-updates,trusty-security,now 2.24.23-0ubuntu1.4 amd64 [installed,automatic]
libgtk2.0-bin/trusty-updates,trusty-security,now 2.24.23-0ubuntu1.4 amd64 [installed,automatic]
libgtk2.0-common/trusty-updates,trusty-security,now 2.24.23-0ubuntu1.4 all [installed,automatic]
```Seems like an Ubuntu LTS with a version as high as 14 would have that included in the base GUI packages, but oh well, if I can work past the issue without re-installing, I'll be happy.

---

### Post by banceu_sergiu_ione on 2016-06-28
If you use the terminal command line by running 
```
sudo apt update
```
```
sudo apt upgrade
```
does it get stuck or do you get any errors while installing?
Put the output if you get errors.

---

### Post by The00Dustin on 2016-06-28
> **banceu_sergiu_ione said:**
> If you use the terminal command line by running 
```
sudo apt update
```
```
sudo apt upgrade
```
does it get stuck or do you get any errors while installing?
Put the output if you get errors.I actually already killed the software updater process and ran those commands from the CLI earlier today.  Here is what I remember:
1) Upon killing the software updater, I got the option to report an appcrash for installation of mdadm.  This could be concerning considering that I do have a mirrored drive setup on this machine.
2) I ran ll /boot/grub and noticed that /boot/grub/grub.cfg was marked last modified at the time of termination of software updater, so it seems likely that the file was held open but not updated due to the unavailable prompt for confirmation.
3) sudo apt update did not have any problems.
4) sudo apt upgrade did not have any problems but did not install any mdadm or grub packages, so I am still concerned about grub and now also concerned about mdadm.

My main concern here is that a reboot is going to leave me unable to access the OS, this could happen if the update issues lead to a with grub or mdadm, so now I'm wondering how best to fix both.  According to the man page for update-grub2 (which is actually the man page for update-grub), that command is a stub command to run another command, so I'm thinking running it couldn't hurt, but I'm not sure if the two stubs would behave differently or not.  Moreover, this doesn't even address any potential mdadm issue.  Is there a way to get apt to re-install a package in order to make sure everything is installed right?  I'm thinking re-installing grub-pc and mdadm might be enough to keep the system bootable if it isn't already.

All of that having been said, in case I haven't covered everything, perhaps this snippet from /var/log/apt/history.log could be useful:```
$ cat /var/log/apt/history.log

Start-Date: 2016-06-22  08:20:48
Commandline: aptdaemon role='role-commit-packages' sender=':1.95'
Upgrade: dpkg:amd64 (1.17.5ubuntu5.5, 1.17.5ubuntu5.6), libdpkg-perl:amd64 (1.17.5ubuntu5.5, 1.17.5ubuntu5.6)
End-Date: 2016-06-22  08:20:52


Start-Date: 2016-06-22  08:24:24
Commandline: aptdaemon role='role-commit-packages' sender=':1.95'
Install: linux-headers-3.19.0-61:amd64 (3.19.0-61.69~14.04.1), linux-image-extra-3.19.0-61-generic:amd64 (3.19.0-61.69~14.04.1), linux-image-3.19.0-61-generic:amd64 (3.19.0-61.69~14.04.1), linux-headers-3.19.0-61-generic:amd64 (3.19.0-61.69~14.04.1)
Upgrade: python3-problem-report:amd64 (2.14.1-0ubuntu3.19, 2.14.1-0ubuntu3.21), oxideqt-codecs:amd64 (1.13.6-0ubuntu0.14.04.1, 1.15.7-0ubuntu0.14.04.1), libnl-genl-3-200:amd64 (3.2.21-1, 3.2.21-1ubuntu3), apt:amd64 (1.0.1ubuntu2.13, 1.0.1ubuntu2.14), libasan0:amd64 (4.8.4-2ubuntu1~14.04.1, 4.8.4-2ubuntu1~14.04.3), libquadmath0:amd64 (4.8.4-2ubuntu1~14.04.1, 4.8.4-2ubuntu1~14.04.3), liblcms2-2:amd64 (2.5-0ubuntu4, 2.5-0ubuntu4.1), gcc-4.8-base:amd64 (4.8.4-2ubuntu1~14.04.1, 4.8.4-2ubuntu1~14.04.3), multiarch-support:amd64 (2.19-0ubuntu6.7, 2.19-0ubuntu6.9), python-samba:amd64 (4.3.8+dfsg-0ubuntu0.14.04.2, 4.3.9+dfsg-0ubuntu0.14.04.3), libssl1.0.0:amd64 (1.0.1f-1ubuntu2.18, 1.0.1f-1ubuntu2.19), apt-transport-https:amd64 (1.0.1ubuntu2.13, 1.0.1ubuntu2.14), libsoup2.4-1:amd64 (2.44.2-1ubuntu2, 2.44.2-1ubuntu2.1), cpp-4.8:amd64 (4.8.4-2ubuntu1~14.04.1, 4.8.4-2ubuntu1~14.04.3), libgomp1:amd64 (4.8.4-2ubuntu1~14.04.1, 4.8.4-2ubuntu1~14.04.3), libdecoration0:amd64 (0.9.11.3+14.04.20150313-0ubuntu1, 0.9.11.3+14.04.20160425-0ubuntu1), libarchive13:amd64 (3.1.2-7ubuntu2.1, 3.1.2-7ubuntu2.2), compiz-gnome:amd64 (0.9.11.3+14.04.20150313-0ubuntu1, 0.9.11.3+14.04.20160425-0ubuntu1), libtsan0:amd64 (4.8.4-2ubuntu1~14.04.1, 4.8.4-2ubuntu1~14.04.3), apt-utils:amd64 (1.0.1ubuntu2.13, 1.0.1ubuntu2.14), thunderbird:amd64 (38.6.0+build1-0ubuntu0.14.04.1, 38.8.0+build1-0ubuntu0.14.04.1), compiz-core:amd64 (0.9.11.3+14.04.20150313-0ubuntu1, 0.9.11.3+14.04.20160425-0ubuntu1), firefox:amd64 (45.0.2+build1-0ubuntu0.14.04.1, 47.0+build3-0ubuntu0.14.04.1), openssh-server:amd64 (6.6p1-2ubuntu2.6, 6.6p1-2ubuntu2.7), libc-dev-bin:amd64 (2.19-0ubuntu6.7, 2.19-0ubuntu6.9), grub-common:amd64 (2.02~beta2-9ubuntu1.7, 2.02~beta2-9ubuntu1.8), libc-bin:amd64 (2.19-0ubuntu6.7, 2.19-0ubuntu6.9), libc6:amd64 (2.19-0ubuntu6.7, 2.19-0ubuntu6.9), mdadm:amd64 (3.2.5-5ubuntu4.2, 3.2.5-5ubuntu4.3), openssh-sftp-server:amd64 (6.6p1-2ubuntu2.6, 6.6p1-2ubuntu2.7), dosfstools:amd64 (3.0.26-1, 3.0.26-1ubuntu0.1), compiz:amd64 (0.9.11.3+14.04.20150313-0ubuntu1, 0.9.11.3+14.04.20160425-0ubuntu1), linux-image-generic-lts-vivid:amd64 (3.19.0.58.41, 3.19.0.61.44), python-libxml2:amd64 (2.9.1+dfsg1-3ubuntu4.7, 2.9.1+dfsg1-3ubuntu4.8), libapt-inst1.5:amd64 (1.0.1ubuntu2.13, 1.0.1ubuntu2.14), libtevent0:amd64 (0.9.26-0ubuntu0.14.04.1, 0.9.28-0ubuntu0.14.04.1), libpoppler-glib8:amd64 (0.24.5-2ubuntu4.3, 0.24.5-2ubuntu4.4), libcompizconfig0:amd64 (0.9.11.3+14.04.20150313-0ubuntu1, 0.9.11.3+14.04.20160425-0ubuntu1), libpoppler44:amd64 (0.24.5-2ubuntu4.3, 0.24.5-2ubuntu4.4), ssh-askpass-gnome:amd64 (6.6p1-2ubuntu2.6, 6.6p1-2ubuntu2.7), libnl-3-200:amd64 (3.2.21-1, 3.2.21-1ubuntu3), klibc-utils:amd64 (2.0.3-0ubuntu1, 2.0.3-0ubuntu1.14.04.1), libgd3:amd64 (2.1.0-3, 2.1.0-3ubuntu0.1), grub2-common:amd64 (2.02~beta2-9ubuntu1.7, 2.02~beta2-9ubuntu1.8), bash-completion:amd64 (2.1-4ubuntu0.1, 2.1-4ubuntu0.2), libatomic1:amd64 (4.8.4-2ubuntu1~14.04.1, 4.8.4-2ubuntu1~14.04.3), lsb-base:amd64 (4.1+Debian11ubuntu6, 4.1+Debian11ubuntu6.1), libspice-server1:amd64 (0.12.4-0nocelt2ubuntu1.2, 0.12.4-0nocelt2ubuntu1.3), samba-common-bin:amd64 (4.3.8+dfsg-0ubuntu0.14.04.2, 4.3.9+dfsg-0ubuntu0.14.04.3), libxml2:amd64 (2.9.1+dfsg1-3ubuntu4.7, 2.9.1+dfsg1-3ubuntu4.8), liboxideqtcore0:amd64 (1.13.6-0ubuntu0.14.04.1, 1.15.7-0ubuntu0.14.04.1), linux-headers-generic-lts-vivid:amd64 (3.19.0.58.41, 3.19.0.61.44), binutils:amd64 (2.24-5ubuntu14, 2.24-5ubuntu14.1), libsoup-gnome2.4-1:amd64 (2.44.2-1ubuntu2, 2.44.2-1ubuntu2.1), lsb-release:amd64 (4.1+Debian11ubuntu6, 4.1+Debian11ubuntu6.1), libnm-util2:amd64 (0.9.8.8-0ubuntu7.2, 0.9.8.8-0ubuntu7.3), samba-libs:amd64 (4.3.8+dfsg-0ubuntu0.14.04.2, 4.3.9+dfsg-0ubuntu0.14.04.3), openssh-client:amd64 (6.6p1-2ubuntu2.6, 6.6p1-2ubuntu2.7), wget:amd64 (1.15-1ubuntu1.14.04.1, 1.15-1ubuntu1.14.04.2), libapt-pkg4.12:amd64 (1.0.1ubuntu2.13, 1.0.1ubuntu2.14), libgcc-4.8-dev:amd64 (4.8.4-2ubuntu1~14.04.1, 4.8.4-2ubuntu1~14.04.3), libnm-glib-vpn1:amd64 (0.9.8.8-0ubuntu7.2, 0.9.8.8-0ubuntu7.3), thunderbird-gnome-support:amd64 (38.6.0+build1-0ubuntu0.14.04.1, 38.8.0+build1-0ubuntu0.14.04.1), gcc-4.8:amd64 (4.8.4-2ubuntu1~14.04.1, 4.8.4-2ubuntu1~14.04.3), linux-generic-lts-vivid:amd64 (3.19.0.58.41, 3.19.0.61.44), grub-pc-bin:amd64 (2.02~beta2-9ubuntu1.7, 2.02~beta2-9ubuntu1.8), grub-pc:amd64 (2.02~beta2-9ubuntu1.7, 2.02~beta2-9ubuntu1.8), smbclient:amd64 (4.3.8+dfsg-0ubuntu0.14.04.2, 4.3.9+dfsg-0ubuntu0.14.04.3), compiz-plugins-default:amd64 (0.9.11.3+14.04.20150313-0ubuntu1, 0.9.11.3+14.04.20160425-0ubuntu1), apport-gtk:amd64 (2.14.1-0ubuntu3.19, 2.14.1-0ubuntu3.21), liboxideqtquick0:amd64 (1.13.6-0ubuntu0.14.04.1, 1.15.7-0ubuntu0.14.04.1), apport:amd64 (2.14.1-0ubuntu3.19, 2.14.1-0ubuntu3.21), libklibc:amd64 (2.0.3-0ubuntu1, 2.0.3-0ubuntu1.14.04.1), liboxideqt-qmlplugin:amd64 (1.13.6-0ubuntu0.14.04.1, 1.15.7-0ubuntu0.14.04.1), libexpat1:amd64 (2.1.0-4ubuntu1.1, 2.1.0-4ubuntu1.3), python3-apport:amd64 (2.14.1-0ubuntu3.19, 2.14.1-0ubuntu3.21), openssl:amd64 (1.0.1f-1ubuntu2.18, 1.0.1f-1ubuntu2.19), libwbclient0:amd64 (4.3.8+dfsg-0ubuntu0.14.04.2, 4.3.9+dfsg-0ubuntu0.14.04.3), poppler-utils:amd64 (0.24.5-2ubuntu4.3, 0.24.5-2ubuntu4.4), libc6-dbg:amd64 (2.19-0ubuntu6.7, 2.19-0ubuntu6.9), network-manager:amd64 (0.9.8.8-0ubuntu7.2, 0.9.8.8-0ubuntu7.3), linux-libc-dev:amd64 (3.13.0-85.129, 3.13.0-88.135), gir1.2-networkmanager-1.0:amd64 (0.9.8.8-0ubuntu7.2, 0.9.8.8-0ubuntu7.3), libtasn1-6:amd64 (3.4-3ubuntu0.3, 3.4-3ubuntu0.4), libnl-route-3-200:amd64 (3.2.21-1, 3.2.21-1ubuntu3), samba-common:amd64 (4.3.8+dfsg-0ubuntu0.14.04.2, 4.3.9+dfsg-0ubuntu0.14.04.3), libstdc++6:amd64 (4.8.4-2ubuntu1~14.04.1, 4.8.4-2ubuntu1~14.04.3), libitm1:amd64 (4.8.4-2ubuntu1~14.04.1, 4.8.4-2ubuntu1~14.04.3), gir1.2-soup-2.4:amd64 (2.44.2-1ubuntu2, 2.44.2-1ubuntu2.1), libc6-dev:amd64 (2.19-0ubuntu6.7, 2.19-0ubuntu6.9), libsmbclient:amd64 (4.3.8+dfsg-0ubuntu0.14.04.2, 4.3.9+dfsg-0ubuntu0.14.04.3), libnm-glib4:amd64 (0.9.8.8-0ubuntu7.2, 0.9.8.8-0ubuntu7.3)
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: 2016-06-28  10:09:42


Start-Date: 2016-06-28  10:11:50
Commandline: apt-get upgrade
Upgrade: dpkg:amd64 (1.17.5ubuntu5.6, 1.17.5ubuntu5.7), libdpkg-perl:amd64 (1.17.5ubuntu5.6, 1.17.5ubuntu5.7), linux-libc-dev:amd64 (3.13.0-88.135, 3.13.0-91.138)
End-Date: 2016-06-28  10:11:54
```

---

### Post by banceu_sergiu_ione on 2016-06-28
If you had run apt update && upgrade and you got upgraded with out any kind of errors, then you can safely reboot.

If you are so concerned about you can not access the OS, this possibility may come some day. You get your self a LiveUSB ubuntu or cd and run it as ' Try without install' , let it log in, connect to Ethernet, google search boot-repair, select the link Boot-Repair-CommunityHelpWiki-Official Ubuntu Documentation and fallow the 2nd option.
But only run a boot repair if needed. If it work is not need to run it. And you can not know if boot work unless you try to boot :)

So, reboot now and after run a clean if you want using ```
sudo apt autoclean
``` and autoremove if want a more deep clean.

---

### Post by The00Dustin on 2016-06-28
OK, I bit the bullet and rebooted.  The system did come up fine (except it came to my attention that mounting of the encrypted swap partition created during standard install is broken and has been for so long I forgot I had a swap partition, but that's an issue for another thread).  uname -a compared to ll /boot and the apt history confirm that I am running the latest kernel, 3.19.0-61.  mount confirms that OS is still mounted on md arrays, and mdadm -D /dev/md? shows all arrays fine.  I'm good to go here, thanks for the help.

---

### Post by banceu_sergiu_ione on 2016-06-29
> **The00Dustin said:**
> ....except it came to my attention that mounting of the encrypted swap partition created during standard install is broken and has been for so long I forgot I had a swap partition, but that's an issue for another thread...

How did you checked thet its not mount?
Its because you see your system not use it ?

Can you put the output of ```
sudo lsblk -l
``` and ```
mount -l
```

---

