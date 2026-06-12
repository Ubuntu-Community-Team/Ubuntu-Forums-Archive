---
title: "udev issue after upgrade from 14.x to 14.10"
date: 2015-02-13
forum: General Help
---

### Post by vijai on 2015-02-13
I am getting following error while trying to install any package. 
I have tried the [http://ubuntuforums.org/showthread.php?t=2187724&page=8](http://ubuntuforums.org/showthread.php?t=2187724&page=8) link for fixing the issue but no luck still.

Can someone help me to fix the issue!! thanks in advance. 


root@RaGhar:/var/cache/apt/archives# dpkg --install ./udev_208-8ubuntu8.2_amd64.deb 
(Reading database ... 382015 files and directories currently installed.)
Preparing to unpack .../udev_208-8ubuntu8.2_amd64.deb ...
Unpacking udev (208-8ubuntu8.2) over (208-8ubuntu8.2) ...
Setting up udev (208-8ubuntu8.2) ...
udev stop/waiting
udev start/running, process 7597
update-initramfs: deferring update (trigger activated)
insserv: warning: script 'K01.depend.start' missing LSB tags and overrides
insserv: script udev-orig: service udev already provided!
insserv: script udev-orig: service mdadm-raid already provided!
insserv: script udev-original: service udev already provided!
insserv: script udev-original: service mdadm-raid already provided!
insserv: There is a loop between service grub-common and mountdevsubfs if started
insserv:  loop involving service mountdevsubfs at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service .depend.start if started
insserv: Starting .depend.start depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.start depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.start depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.start depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.start depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.start depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.start depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.start depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package udev (--install):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for man-db (2.7.0.2-2) ...
Errors were encountered while processing:
 udev

---

