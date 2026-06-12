---
title: "LTSP boot problem with Dell Vostro 200 and 82562v-2 Intel/Dell Network card"
date: 2007-09-16
forum: General Help
---

### Post by jmbarreto on 2007-09-16
Hi... I've setup successfully an LTSP server with Feisty;  both server and clients are i386 arch;  recently we bought some new clients from dell (cheap dell vostro 200) and those have the 82562v-2 Intel/Dell network card;  the problem that I've found is that that particular card is not "recognized" during boot (after successfully pxe-boot and aquired the Ip) and the client panic during initial nic configuration;  the exact error that I have during client's boot is: 

[FONT="Courier New"]Loading, please wait...
ipconfig: eth0: SIOCGIFINDEX: No such device
ipconfig: no devices to configure
/init: .: 1: Can't open /tmp/net-eth0.conf
[   27.323320] Kernel panic - not syncing: Attempted to kill init!
[   27.323375] [/FONT]

I have done already all the updates/upgrades on the server, and completely re-built the ltsp chroot image;  I've done some browsing and have found a bug ([https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.20/+bug/121187](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.20/+bug/121187)) which I'm not sure is related or not... I've tryed with the live CD and either the card is recognized;  I'm wondering that some modprobe/insmod will be necessary on the LTSP chroot env, but I'm completely lost at this point.

ANY help will be really appreciated...

---

### Post by jmbarreto on 2007-09-22
Well, for those who might be interested, I have found the solution, which is compile the driver into the ltsp chroot and re-build the initramfs;  have used some of the instructions provided on:

[https://help.ubuntu.com/community/HowToSetupLTSPDevelEnvironment](https://help.ubuntu.com/community/HowToSetupLTSPDevelEnvironment)

For complete instructions on how-to build the driver in general (for those interested in driver for Intel 82562v-2 NIC installed on Dell Vostro 200 and maybe other HW) :

[http://ubuntuforums.org/showthread.php?t=551720](http://ubuntuforums.org/showthread.php?t=551720)

HTH.

---

