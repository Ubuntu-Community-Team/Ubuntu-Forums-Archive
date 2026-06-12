---
title: "Ubuntu 14.04 64-bit won't open console"
date: 2014-08-19
forum: General Help
---

### Post by bulrush2 on 2014-08-19
[LIST=1]
[*]Server config: Ubuntu 14.04 64-bit running as a VM under Vsphere 5.5.0 as 10.19.3.13 
[*]Ubuntu: uname -a gives: Linux ubuntucomp 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux 
[*]VSphere runs under Windows 7 (32-bit) with 4GB ram, Intel Core 2 Duo CPU E8500 @ 3.16ghz 
[*]Client PC: Windows 7 running Putty 0.63 and Xming 6.9.0.31 and Exceed 14.0 (another Xserver) 
[/LIST]


I'm trying to configure Samba which is no longer working, so I went to the console on the VM, and the console won't open. I just see a black screen. Using Putty from my Win 7 PC connects me to Ubuntu. 

I just noticed that the VM, called VSphere, is running under Windows 7, which is 32-bit, and Ubuntu is 64-bit. Is this a problem? Could this be the root of many of my problems? 

Also, samba seems to be borked on Ubuntu 14.04. See [http://discourse.ubuntu.com/t/samba-in-14-04-broken/1301](http://discourse.ubuntu.com/t/samba-in-14-04-broken/1301). I'm considering installing Ubuntu 13.10. Are there any serious problems with that idea? I've spent 15 days trying to get this to work with only 4 days of use. 

I'm not stupid, but I am ignorant about Ubuntu. I've read dozes of web pages, a minimum of 8 regarding Samba, with limited success.

---

### Post by bulrush2 on 2014-08-19
Made a new thread to show how I got samba working: [http://ubuntuforums.org/showthread.php?t=2240326&p=13102432](http://ubuntuforums.org/showthread.php?t=2240326&p=13102432)

But console still won't open on machine running VSphere.

---

