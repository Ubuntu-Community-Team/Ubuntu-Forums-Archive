---
title: "problem of launch startx"
date: 2018-04-01
forum: General Help
---

### Post by penapisemnet on 2018-04-01
Hello!

i installed 
```
sudo apt-get install gnome-shell
```

then i want to launch this graphical shell

```
 # startx
```

and instead the lounch it messages
```

X.Org X Server 1.18.4
Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-97-generic x86_64 Ubuntu
Current Operating System: Linux ubuntu-8gb-fsn1-dc8-1 4.4.0-116-generic #140-Ubuntu SMP Mon Feb 12 21:23:04 UTC 2018 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-116-generic root=UUID=f52e67a1-0b81-407e-9f4c-a4b9439bf08b ro consoleblank=0 systemd.show_status=true elevator=noop console=tty1 console=ttyS0
Build Date: 13 October 2017  01:57:05PM
xorg-server 2:1.18.4-0ubuntu0.7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.33.6
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr  1 12:16:21 2018
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) 
Fatal server error:
(EE) no screens found(EE) 
(EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE) 
(EE) Server terminated with error (1). Closing log file.
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
```



How is to solve this problem?

Thank you for help in advance.

---

### Post by deadflowr on 2018-04-01
You need to properly set it up.
Something like what is mentioned here:
[https://wiki.archlinux.org/index.php/GNOME#Manually]("https://wiki.archlinux.org/index.php/GNOME#Manually")

Also, Since I see the #, does this mean you are trying to do this as root?
If so, don't.
Gnome shell is not really root friendly.
Best to run it as your normal user.

We would also like users to abide by this:
[https://ubuntuforums.org/showthread.php?t=1486138]("https://ubuntuforums.org/showthread.php?t=1486138")

Hope it helps move you along.

---

