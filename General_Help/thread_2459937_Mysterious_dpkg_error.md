---
title: "Mysterious dpkg error"
date: 2021-03-29
forum: General Help
---

### Post by nkarp on 2021-03-29
Hi, I'm new to Linux, was going through a tutorial, and came up with what appears to be some kind of configuration error?:

```
nrk@lambda:~$ sudo apt install cowsay
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  filters cowsay-off
The following NEW packages will be installed:
  cowsay
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0 B/18.5 kB of archives.
After this operation, 93.2 kB of additional disk space will be used.
Selecting previously unselected package cowsay.
(Reading database ... 270994 files and directories currently installed.)
Preparing to unpack .../cowsay_3.03+dfsg2-7_all.deb ...
Unpacking cowsay (3.03+dfsg2-7) ...
Setting up lvm2 (2.03.07-1ubuntu1) ...
update-initramfs: deferring update (trigger activated)
Failed to restart lvm2-lvmpolld.service: Unit lvm2-lvmpolld.socket is masked.
invoke-rc.d: initscript lvm2-lvmpolld, action "restart" failed.
&#9679; lvm2-lvmpolld.service - LVM2 poll daemon
     Loaded: loaded (/lib/systemd/system/lvm2-lvmpolld.service; static; vendor preset: enabled)
     Active: inactive (dead)
       Docs: man:lvmpolld(8)
dpkg: error processing package lvm2 (--configure):
 installed lvm2 package post-installation script subprocess returned error exit status 1
Setting up cowsay (3.03+dfsg2-7) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for initramfs-tools (0.136ubuntu6.4) ...
update-initramfs: Generating /boot/initrd.img-5.4.0-70-generic
Errors were encountered while processing:
 lvm2
E: Sub-process /usr/bin/dpkg returned an error code (1)


```
Is this something worth worrying about? If so, any advice on how to fix it? (I tried looking at the [COLOR=#000000][FONT=Menlo]lvmpolld[/FONT][/COLOR] man page, per the error message, but had no idea what any of it meant.)

Any help much appreciated - thanks a lot!

[[COLOR=#000000][FONT=Menlo]Ubuntu 20.04.2 LTS][/FONT][/COLOR]

---

### Post by CelticWarrior on 2021-03-29
Welcome.

Perhaps this: [https://askubuntu.com/questions/1049727/every-time-i-install-or-remove-a-package-i-get-lvm2-error](https://askubuntu.com/questions/1049727/every-time-i-install-or-remove-a-package-i-get-lvm2-error)

---

