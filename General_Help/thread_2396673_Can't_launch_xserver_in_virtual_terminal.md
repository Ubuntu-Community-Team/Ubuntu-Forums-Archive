---
title: "Can't launch xserver in virtual terminal"
date: 2018-07-19
forum: General Help
---

### Post by Axis Mann on 2018-07-19
I can no longer launch xserver in a virtual terminal.  I've tried on  tty1, tty2, tty3,...,etc, adnaseaum.  The command xinit -- :1 use to  work as expected.  

But now, I just get a fatal server error: parse_vt_settings: Cannot open /dev/tty0 (permissions).  

I have three different installations: 14.04 with X server 1.17.2, 14.04  with xserver 1.18.3, and 16.04 with xserver 1.18.4.  I first noticed  this problem on new install of 14.04 with X server 1.18.3 on a separate  machine.

I never updated a prior install of ubuntu 14.04 which still runs X  server 1.17.2.  The prior install of 14.04  still executes the xinit --  :1 as expected. I checked my 16.04  install  which is using  X server  1.18.4 (on same machine with working 14.04) and found it suffered the  same problem as the new install of 14.04 running X server 1.18.3 (ie it won't execute xinit -- :1 without the fatal server error).

How would I go about diagnosing and correcting this problem in a manner even a newbie would understand?

---

### Post by HermanAB on 2018-07-19
Err... version 14 uses Wayland?

---

### Post by Axis Mann on 2018-07-19
Not sure.  Doen't this mean I'm running some version of X11?

[   497.936]  X.Org X Server 1.18.3 Release Date: 2016-04-04
[   497.936] X Protocol Version 11, Revision 0
[   497.936] Build Operating System: Linux 4.4.0-97-generic x86_64 Ubuntu
[   497.936] Current Operating System: Linux Mimas 4.4.0-130-generic #156~14.04.1-Ubuntu SMP Thu Jun 14 13:51:47 UTC 2018 x86_64
[   497.936] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-130-generic.efi.signed root=UUID=884720ee-1747-404f-a1fa-17d5526ef519 ro quiet splash nomdmonddf nomdmonisw vt.handoff=7
[   497.937] Build Date: 13 October 2017  02:07:47PM
[   497.937] xorg-server 2:1.18.3-1ubuntu2.3~trusty4 (For technical support please see [http://ww](http://ww)

---

### Post by Axis Mann on 2018-07-20
See launchpad bug report [https://bugs.launchpad.net/ubuntu/+source/xinit/+bug/1562219](https://bugs.launchpad.net/ubuntu/+source/xinit/+bug/1562219).  Don't know if that means the same thing as my problem but a description similar to mine did appear in one of the comments (ie Cannot open /dev/tty0 (permission denied).  I tried using suggested command line switch with my xinit command (xinit -- :1 vt1) but that didn't work by itself.  

I also installed package xserver-xorg-legacy to re-enable the xinit command after it stopped working following an xorg (I think) update.  But that only worked for my ubuntu 16.04 32-bit installation.  It didn't work for my ubuntu 14.04 64-bit installation because I couldn't get that package to install.  Instead, I got message Package xserver-xorg-legacy:i386 is not available, but is referred to by another package.  I tried runing apt-get update but that that didn't help resolve the message.  

I still can't launch an xserver in a virtual terminal for my ubuntu 14.04 64-bit machine.  None of the other comments in the bug report seemed applicable.  But what I know?

---

### Post by kazakore on 2018-07-20
> **HermanAB said:**
> Err... version 14 uses Wayland?

I think only 17.10 ever came with Wayland.....

---

### Post by deadflowr on 2018-07-20
> **kazakore said:**
> I think only 17.10 ever came with Wayland.....

17.10 and newer.
17.10 defaulted to use Wayland as the login.
But they reverted to defaulting logins to X for 18.04 (not sure what they'll do beyond that, whether or not they default to X or Wayland; it's too soon to tell.)

18.04 has Wayland installed and ready, it's just not the default login option.
fwiw


(And I'm out since I only wanted to comment on that)

---

### Post by kazakore on 2018-07-20
> **deadflowr said:**
> 17.10 and newer.
17.10 defaulted to use Wayland as the login.
But they reverted to defaulting logins to X for 18.04 (not sure what they'll do beyond that, whether or not they default to X or Wayland; it's too soon to tell.)

18.04 has Wayland installed and ready, it's just not the default login option.
fwiw


(And I'm out since I only wanted to comment on that)


You sure??? Maybe vanilla Ubuntu does but it's definitely not a core part installed on all flavours.


```
$ apt-cache policy wayla #[tab][tab]
$ apt-cache policy wayland-protocols 
wayland-protocols:
  Installed: (none)
  Candidate: 1.13-1
  Version table:
     1.13-1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
        500 http://gb.archive.ubuntu.com/ubuntu bionic/main i386 Packages

```

```
$ apt-cache policy *wayland*
libwayland-egl1:
  Installed: (none)
  Candidate: (none)
  Version table:
freerdp2-wayland:
  Installed: (none)
  Candidate: 2.0.0~git20170725.1.1648deb+dfsg1-7
  Version table:
     2.0.0~git20170725.1.1648deb+dfsg1-7 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
libqt5waylandcompositor5-dev:
  Installed: (none)
  Candidate: 5.9.5-0ubuntu1
  Version table:
     5.9.5-0ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
libglfw3-wayland:
  Installed: (none)
  Candidate: 3.2.1-1
  Version table:
     3.2.1-1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
gnome-session-wayland:
  Installed: (none)
  Candidate: 3.28.1-0ubuntu3
  Version table:
     3.28.1-0ubuntu3 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages
        500 http://gb.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages
     3.28.1-0ubuntu2 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe i386 Packages
qtwayland5:
  Installed: 5.9.5-0ubuntu1
  Candidate: 5.9.5-0ubuntu1
  Version table:
 *** 5.9.5-0ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        100 /var/lib/dpkg/status
libkf5wayland-dev:
  Installed: (none)
  Candidate: 4:5.44.0-0ubuntu1
  Version table:
     4:5.44.0-0ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
wayland-protocols:
  Installed: (none)
  Candidate: 1.13-1
  Version table:
     1.13-1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
        500 http://gb.archive.ubuntu.com/ubuntu bionic/main i386 Packages
ibus-wayland:
  Installed: (none)
  Candidate: 1.5.17-3ubuntu4
  Version table:
     1.5.17-3ubuntu4 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
kwin-wayland-backend-x11:
  Installed: (none)
  Candidate: 4:5.12.6-0ubuntu0.1
  Version table:
     4:5.12.6-0ubuntu0.1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages
     4:5.12.4-0ubuntu2 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
glmark2-es2-wayland:
  Installed: (none)
  Candidate: 2014.03+git20150611.fa71af2d-0ubuntu4
  Version table:
     2014.03+git20150611.fa71af2d-0ubuntu4 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
libqt5waylandcompositor5:
  Installed: 5.9.5-0ubuntu1
  Candidate: 5.9.5-0ubuntu1
  Version table:
 *** 5.9.5-0ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        100 /var/lib/dpkg/status
libkf5waylandclient5:
  Installed: 4:5.44.0-0ubuntu1
  Candidate: 4:5.44.0-0ubuntu1
  Version table:
 *** 4:5.44.0-0ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        100 /var/lib/dpkg/status
libqt5waylandclient5:
  Installed: 5.9.5-0ubuntu1
  Candidate: 5.9.5-0ubuntu1
  Version table:
 *** 5.9.5-0ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        100 /var/lib/dpkg/status
qtwayland5-doc:
  Installed: (none)
  Candidate: 5.9.5-0ubuntu1
  Version table:
     5.9.5-0ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe i386 Packages
kwayland-dev:
  Installed: (none)
  Candidate: 4:5.44.0-0ubuntu1
  Version table:
     4:5.44.0-0ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe i386 Packages
plasma-workspace-wayland:
  Installed: (none)
  Candidate: 4:5.12.6-0ubuntu0.1
  Version table:
     4:5.12.6-0ubuntu0.1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages
     4:5.12.4-0ubuntu3 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
libwayland0:
  Installed: (none)
  Candidate: (none)
  Version table:
glmark2-wayland:
  Installed: (none)
  Candidate: 2014.03+git20150611.fa71af2d-0ubuntu4
  Version table:
     2014.03+git20150611.fa71af2d-0ubuntu4 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
gammaray-plugin-waylandinspector:
  Installed: (none)
  Candidate: 2.7.0-1ubuntu8
  Version table:
     2.7.0-1ubuntu8 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
qtwayland5-dev-tools:
  Installed: (none)
  Candidate: 5.9.5-0ubuntu1
  Version table:
     5.9.5-0ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
libwayland-client0:
  Installed: 1.14.0-2
  Candidate: 1.14.0-2
  Version table:
 *** 1.14.0-2 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
        100 /var/lib/dpkg/status
kwayland-data:
  Installed: 4:5.44.0-0ubuntu1
  Candidate: 4:5.44.0-0ubuntu1
  Version table:
 *** 4:5.44.0-0ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe i386 Packages
        100 /var/lib/dpkg/status
libwayland-bin:
  Installed: 1.14.0-2
  Candidate: 1.14.0-2
  Version table:
 *** 1.14.0-2 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
        100 /var/lib/dpkg/status
libqt5waylandclient5-dev:
  Installed: (none)
  Candidate: 5.9.5-0ubuntu1
  Version table:
     5.9.5-0ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
libwayland-dev:
  Installed: 1.14.0-2
  Candidate: 1.14.0-2
  Version table:
 *** 1.14.0-2 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
        100 /var/lib/dpkg/status
libwayland-doc:
  Installed: (none)
  Candidate: 1.14.0-2
  Version table:
     1.14.0-2 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
        500 http://gb.archive.ubuntu.com/ubuntu bionic/main i386 Packages
xwayland-hwe-16.04:
  Installed: (none)
  Candidate: 3:14.1
  Version table:
     3:14.1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
kwayland-integration:
  Installed: 4:5.12.4-0ubuntu1
  Candidate: 4:5.12.4-0ubuntu1
  Version table:
 *** 4:5.12.4-0ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        100 /var/lib/dpkg/status
kwin-wayland-backend-fbdev:
  Installed: (none)
  Candidate: 4:5.12.6-0ubuntu0.1
  Version table:
     4:5.12.6-0ubuntu0.1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages
     4:5.12.4-0ubuntu2 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
kwin-wayland:
  Installed: (none)
  Candidate: 4:5.12.6-0ubuntu0.1
  Version table:
     4:5.12.6-0ubuntu0.1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages
     4:5.12.4-0ubuntu2 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
libwayland-egl1-mesa:
  Installed: 18.0.5-0ubuntu0~18.04.1
  Candidate: 18.0.5-0ubuntu0~18.04.1
  Version table:
 *** 18.0.5-0ubuntu0~18.04.1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     18.0.0~rc5-1ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
libkf5waylandserver5:
  Installed: (none)
  Candidate: 4:5.44.0-0ubuntu1
  Version table:
     4:5.44.0-0ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
qtwayland5-doc-html:
  Installed: (none)
  Candidate: 5.9.5-0ubuntu1
  Version table:
     5.9.5-0ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe i386 Packages
xwayland:
  Installed: (none)
  Candidate: 2:1.19.6-1ubuntu4
  Version table:
     2:1.19.6-1ubuntu4 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
libva-wayland2:
  Installed: 2.1.0-3
  Candidate: 2.1.0-3
  Version table:
 *** 2.1.0-3 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        100 /var/lib/dpkg/status
kwin-wayland-backend:
  Installed: (none)
  Candidate: (none)
  Version table:
qml-module-qtwayland-compositor:
  Installed: (none)
  Candidate: 5.9.5-0ubuntu1
  Version table:
     5.9.5-0ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
kwin-wayland-backend-virtual:
  Installed: (none)
  Candidate: 4:5.12.6-0ubuntu0.1
  Version table:
     4:5.12.6-0ubuntu0.1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages
     4:5.12.4-0ubuntu2 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
qtwayland5-examples:
  Installed: (none)
  Candidate: 5.9.5-0ubuntu1
  Version table:
     5.9.5-0ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
kwin-wayland-backend-drm:
  Installed: (none)
  Candidate: 4:5.12.6-0ubuntu0.1
  Version table:
     4:5.12.6-0ubuntu0.1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages
     4:5.12.4-0ubuntu2 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
kwin-wayland-backend-wayland:
  Installed: (none)
  Candidate: 4:5.12.6-0ubuntu0.1
  Version table:
     4:5.12.6-0ubuntu0.1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages
     4:5.12.4-0ubuntu2 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
libwayland-server0:
  Installed: 1.14.0-2
  Candidate: 1.14.0-2
  Version table:
 *** 1.14.0-2 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
        100 /var/lib/dpkg/status
libwayland-cursor0:
  Installed: 1.14.0-2
  Candidate: 1.14.0-2
  Version table:
 *** 1.14.0-2 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
        100 /var/lib/dpkg/status
```

So a small number of the libraries for Wayland installed but no backend from what I can see from a Studio install....

---

### Post by deadflowr on 2018-07-20
I'm referring to Ubuntu.
Flavors do their own things in terms of login sessions.
And from what I know only Ubuntu and Kubuntu have Wayland login options 
(maybe budgie does, but I don't use that, so...)

Reference:
[https://blog.ubuntu.com/2018/01/26/bionic-beaver-18-04-lts-to-use-xorg-by-default]("https://blog.ubuntu.com/2018/01/26/bionic-beaver-18-04-lts-to-use-xorg-by-default")
> The Wayland session will still be available, pre-installed, for people to use, but for our &#8216;out of the box&#8217; users the Ubuntu experience needs to be stable and provide the features they have come to expect and use in daily life and Xorg is the best choice here, at least for 18.04 LTS, but for 18.10 we will re-evaluate Wayland as the default.

---

### Post by Axis Mann on 2018-07-21
I got no wayland server on my machine.  It's strictly Xorg.  I've confirmed that my initial load of ubuntu 14.04 would run xinit in a vitual terminal as expected with command xinit --:1 but would no longer launch xinit without error after all current updates were applied.

I also discovered that xinit wouldn't launch in a virtual terminal on my 16.04 32 bit installation.

I was able to install xserver-xorg-legacy package to kind of resolve the problem on the 16.04 installation except that I now need to launch xserver with an extra option as  in command xinit -- :1 vt1 but don't have a similar solution for ubuntu 14.04.

Still hacking at it!  Maybe I need bigger machete?  No more comments about Wayland please.

---

### Post by Axis Mann on 2018-07-22
The commmand

     chmod ug+s /usr/lib/xorg/Xorg

fixed the problem on my 14.04 installation.  Needed to reboot before the change had any affect.  Similar solution worked for 16.04 too after I purged the xserver-xorg-legacy package I originally installed to fix the problem in 16.04. 

 I found comment at [https://www.x.org/wiki/FAQMiscellaneous/](https://www.x.org/wiki/FAQMiscellaneous/) addressing [FONT=Liberation Sans, sans-serif]How do I set the correct permissions of my Xserver binary.

This problem is resolved for me.[/FONT]

---

