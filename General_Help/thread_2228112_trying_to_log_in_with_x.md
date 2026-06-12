---
title: "trying to log in with x"
date: 2014-06-05
forum: General Help
---

### Post by jj4 on 2014-06-05
I cannot get the graphical interface up.
I get the following error about a screen:

```

ubuntu@ubuntu:~$ ssh -X root@x.x.x.x
root@88.xx.x.x.x's password: 
Welcome to Ubuntu 12.04.4 LTS (GNU/Linux 3.14.5-x86_64-linode42 x86_64)

 * Documentation:  https://help.ubuntu.com/

  System information as of Thu Jun  5 22:34:17 UTC 2014

  System load:  0.43              Processes:           76
  Usage of /:   2.6% of 47.03GB   Users logged in:     1
  Memory usage: 7%                IP address for eth0: 88.xx.xx.xx.x
  Swap usage:   0%

  Graph this data and manage this system at:
    https://landscape.canonical.com/

*** System restart required ***
Last login: Thu Jun  5 22:29:20 2014 from xxxxxxxx
root@localhost:~# x
x: command not found
root@localhost:~# X

X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
Current Operating System: Linux localhost 3.14.5-x86_64-linode42 #1 SMP Thu Jun 5 15:22:13 EDT 2014 x86_64
Kernel command line: root=/dev/xvda xencons=tty console=tty1 console=hvc0 nosep nodevfs ramdisk_size=32768 ip_conntrack.hashsize=8192 nf_conntrack.hashsize=8192 ro  devtmpfs.mount=1 
Build Date: 16 October 2013  04:41:23PM
xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.30.2
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun  5 22:35:24 2014
(==) Using system config directory "/usr/share/X11/xorg.conf.d"

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
Server terminated with error (1). Closing log file.
root@localhost:~# 



```

I installed teamviewer but obviously because I cannot see the screen I can't see the teamviewr login to use either! :)

---

### Post by TheFu on 2014-06-05
I don't think X works that way - at least I've never used it the way you are trying.

If you want to run an xterm on a remote system, use 
**ssh -X user@remote xterm &**
Of course, the local machine must have X/Windows running (an X-Server to be exact).  The remote system only has X-clients ... basically any GUI-desktop app.
Does that make sense?

Don't connect at root. That is bad form 99.9999999999999999999999% of the time. Use a normal userid, then sudo as needed

Oh ... and your machine needs to be rebooted.

---

