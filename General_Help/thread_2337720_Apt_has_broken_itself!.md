---
title: "Apt has broken itself!"
date: 2016-09-21
forum: General Help
---

### Post by julian-blnc on 2016-09-21
Hey all!

I seem to be having a problem where apt has broken itself.

dpkg is constally failing and I cant really do much of anything.

Here is the error message I am getting

```
julian@alexaPortable:~$ sudo apt autoremoveReading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up udev (229-4ubuntu8) ...
Adding group `input' (GID 106) ...
Done.
update-initramfs: deferring update (trigger activated)
insserv: warning: script 'K07smfpd' missing LSB tags and overrides
insserv: warning: script 'smfpd' missing LSB tags and overrides
insserv: There is a loop between service plymouth and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service plymouth if started
insserv: There is a loop between service smfpd and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service smfpd if started
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: There is a loop between service plymouth and urandom if started
insserv:  loop involving service urandom at depth 4
insserv:  loop involving service mountdevsubfs at depth 2
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service smfpd and dns-clean if started
insserv:  loop involving service dns-clean at depth 1
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting smfpd depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package udev (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for initramfs-tools (0.122ubuntu8.1) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-38-generic
Errors were encountered while processing:
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

Any one run into this before?
I have tried a few diffrent things and even removing the input group but it doesnt seem to want to work again.

---

### Post by yetimon_64 on 2016-09-21
I haven't seen this sort of problem myself, but did find a similar situation posted at the next link that may be of some help (it involves cups-browsed while your situation involves smfpd) ... [http://unix.stackexchange.com/questions/289667/unable-to-install-anything-using-apt-get-because-of-insserv](http://unix.stackexchange.com/questions/289667/unable-to-install-anything-using-apt-get-because-of-insserv)

In that case the person purged then reinstalled cups and that fixed the problem there. The accepted answer though may contain some information that may help you understand what has happened and work out how to fix this. Whatever program that supplies smfpd and K07smfpd scripts (which are missing LSB tags and overrides) may need to be reinstalled. I can't find any reference to those scripts in "apt-cache search" on 14.04 though. 

Which release are you using ? 16.04 ?

---

### Post by mc4man on 2016-09-21
smfpd is some samsung printer driver daemon. So you could move (mv) the script to a .bak, then do your update, then mv back or edit it to add a LSB header defining it's dependencies.
Should be in the  /etc/init.d/ folder

---

### Post by ian-weisser on 2016-09-21
The LSB header on /etc/init.d/smfpd is invalid.
Show us the first 10 lines of that file, and we can probably tell you how to fix it.

---

