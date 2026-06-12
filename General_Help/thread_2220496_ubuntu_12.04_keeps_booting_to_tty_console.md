---
title: "ubuntu 12.04 keeps booting to tty console"
date: 2014-04-28
forum: General Help
---

### Post by ankeshairon88 on 2014-04-28
i was trying to install xdmx & the last thing that I did was deleting the ~/.XAuthority* files since I was getting error in locking authority file. On rebooting, I found myself on this screen.

I tried ```
startx
``` but I get errors. Here's the output:

```
xauth:  error in locking authority file /home/ankesh/.Xauthority
xauth:  error in locking authority file /home/ankesh/.Xauthority


X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
Current Operating System: Linux mindreader 3.11.0-20-generic #34~precise1-Ubuntu SMP Thu Apr 3 17:25:07 UTC 2014 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-20-generic.efi.signed root=UUID=a6d7d9bd-c1c4-4be9-96eb-8a54e6e71354 ro quiet splash vt.handoff=7
Build Date: 16 October 2013  04:41:23PM
xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.30.2
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 28 01:56:05 2014
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/etc/X11/xorg.conf.d"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
Server terminated with error (1). Closing log file.
xinit: giving up
xinit: unable to connect to X server: No such file or directory
xinit: server error
xauth:  error in locking authority file /home/ankesh/.Xauthority

```

I also tried reinstalling Xorg but that didn't help either.

```
echo $DISPLAY
``` gives nothing.

I'd really appreciate any help I can get with this. Thanks

---

